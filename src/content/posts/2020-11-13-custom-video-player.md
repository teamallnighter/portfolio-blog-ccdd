---
template: blog-post
title: Custom Video Player
slug: /javascript/video-player
date: 2020-11-12 22:49
description: JavaScript Developer Edmonton
featuredImage: /assets/custom-webdev-yyc.png
---
## Project: Custom Video Player

##### Build: HTML, CSS, Vanilla JavaScript

##### Features: Custom Video Player, Custom Buttons, Awesome Background

##### Deployment: Github / Netlify

<https://custom-video-player-ccdd.netlify.app/>

- - -

## HTML

```html
<body>
    <h1>Custom Video Player</h1>
    <video 
        src="videos/pbj.mp4" 
        id="video" 
        class="screen" 
        poster="img/poster.png">
    </video>
    <div class="controls">
        <button class="btn" id="play">
            <i class="fa fa-play fa-2x"></i>
        </button>
        <button class="btn" id="stop">
            <i class="fa fa-stop fa-2x"></i>
        </button>
        <input type="range" name="range" id="progress" class="progress" min="0" max="100" step="0.1" value="0"/>
        <span class="timestamp" id="timestamp">00:00</span>
    </div>
    <script src="script.js"></script>
</body>
```

## CSS

```css
@import url('https://fonts.googleapis.com/css?family=Questrial&display=swap');

* {
  box-sizing: border-box;
}

body {
  font-family: 'Questrial', sans-serif;
  background-image: url('../img/poster.png');
  background-repeat: no-repeat;
  background-size: cover;
  background-color: rgb(218, 213, 213);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  max-height: 1000vh;
  margin: 0;
}

h1 {
  color: rgb(255, 255, 255);
}

.screen {
  cursor: pointer;
  width: 60%;
  background-color: rgb(255, 255, 255) !important;
  border-radius: 30px;
  border-style: solid;
  border-color: white;
  border-width: 5px;;
  box-shadow: 2px 4px 8px grey;
}

.controls {
  margin-top: 10vh;
  background: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
  width: 60%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px;
  border-radius: 20px;
  box-shadow: 2px 4px 8px grey;

}

.controls .btn {
  border: 0;
  background: #1b1b1b00;
  cursor: pointer;

}

.controls .fa-play {
  color: #48ff00;
  margin-right: 10px;
}

.controls .fa-play:hover{
  text-shadow:2px 4px 8px grey;
}

.controls .fa-stop {
  color: #f10303;
  margin-right: 10px;

}

.controls .fa-stop:hover{
  text-shadow:2px 4px 8px grey;
}

.controls .fa-pause {
  color: rgb(0, 0, 0);
}

.controls .fa-pause:hover{
  text-shadow:2px 4px 8px grey;
}



.controls .timestamp {
  color: rgb(0, 0, 0);
  font-weight: bold;
  margin-left: 10px;
}

.btn:focus {
  outline: 0;
}

@media (max-width: 800px) {
  .screen,
  .controls {
    width: 90%;
  }
}
```

\## JavaScript

```javascript
const video = document.getElementById('video');
const play = document.getElementById('play');
const stop = document.getElementById('stop');
const progress = document.getElementById('progress');
const timestamp = document.getElementById('timestamp');

// Play & pause video
function toggleVideoStatus() {
  if (video.paused) {
    video.play();
  } else {
    video.pause();
  }
}

// update play/pause icon
function updatePlayIcon() {
  if (video.paused) {
    play.innerHTML = '<i class="fa fa-play fa-2x"></i>';
  } else {
    play.innerHTML = '<i class="fa fa-pause fa-2x"></i>';
  }
}

// Update progress & timestamp
function updateProgress() {
  progress.value = (video.currentTime / video.duration) * 100;

  // Get minutes
  let mins = Math.floor(video.currentTime / 60);
  if (mins < 10) {
    mins = '0' + String(mins);
  }

  // Get seconds
  let secs = Math.floor(video.currentTime % 60);
  if (secs < 10) {
    secs = '0' + String(secs);
  }

  timestamp.innerHTML = `${mins}:${secs}`;
}

// Set video time to progress
function setVideoProgress() {
  video.currentTime = (+progress.value * video.duration) / 100;
}

// Stop video
function stopVideo() {
  video.currentTime = 0;
  video.pause();
}

// Event listeners
video.addEventListener('click', toggleVideoStatus);
video.addEventListener('pause', updatePlayIcon);
video.addEventListener('play', updatePlayIcon);
video.addEventListener('timeupdate', updateProgress);

play.addEventListener('click', toggleVideoStatus);

stop.addEventListener('click', stopVideo);

progress.addEventListener('change', setVideoProgress);
```

\---

I used some CSS from [CSS Tricks](https://css-tricks.com/styling-cross-browser-compatible-range-inputs-css) for the progress bar

```css
/* SOURCE: https://css-tricks.com/styling-cross-browser-compatible-range-inputs-css/ */

input[type='range'] {
	-webkit-appearance: none; /* Hides the slider so that custom slider can be made */
	width: 100%; /* Specific width is required for Firefox. */
	background: transparent; /* Otherwise white in Chrome */
}

input[type='range']::-webkit-slider-thumb {
	-webkit-appearance: none;
}

input[type='range']:focus {
	outline: none; /* Removes the blue border. You should probably do some kind of focus styling for accessibility reasons though. */
}

input[type='range']::-ms-track {
	width: 100%;
	cursor: pointer;

	/* Hides the slider so custom styles can be added */
	background: transparent;
	border-color: transparent;
	color: transparent;
}

/* Special styling for WebKit/Blink */
input[type='range']::-webkit-slider-thumb {
	-webkit-appearance: none;
	border: 1px solid #000000;
	height: 36px;
	width: 16px;
	border-radius: 3px;
	background: #ffffff;
	cursor: pointer;
	margin-top: -14px; /* You need to specify a margin in Chrome, but in Firefox and IE it is automatic */
	box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d; /* Add cool effects to your sliders! */
}

/* All the same stuff for Firefox */
input[type='range']::-moz-range-thumb {
	box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
	border: 1px solid #000000;
	height: 36px;
	width: 16px;
	border-radius: 3px;
	background: #ffffff;
	cursor: pointer;
}

/* All the same stuff for IE */
input[type='range']::-ms-thumb {
	box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
	border: 1px solid #000000;
	height: 36px;
	width: 16px;
	border-radius: 3px;
	background: #ffffff;
	cursor: pointer;
}

input[type='range']::-webkit-slider-runnable-track {
	width: 100%;
	height: 8.4px;
	cursor: pointer;
	box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
	background: #3071a9;
	border-radius: 1.3px;
	border: 0.2px solid #010101;
}

input[type='range']:focus::-webkit-slider-runnable-track {
	background: #367ebd;
}

input[type='range']::-moz-range-track {
	width: 100%;
	height: 8.4px;
	cursor: pointer;
	box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
	background: #3071a9;
	border-radius: 1.3px;
	border: 0.2px solid #010101;
}

input[type='range']::-ms-track {
	width: 100%;
	height: 8.4px;
	cursor: pointer;
	background: transparent;
	border-color: transparent;
	border-width: 16px 0;
	color: transparent;
}
input[type='range']::-ms-fill-lower {
	background: #2a6495;
	border: 0.2px solid #010101;
	border-radius: 2.6px;
	box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
}
input[type='range']:focus::-ms-fill-lower {
	background: #3071a9;
}
input[type='range']::-ms-fill-upper {
	background: #3071a9;
	border: 0.2px solid #010101;
	border-radius: 2.6px;
	box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
}
input[type='range']:focus::-ms-fill-upper {
	background: #367ebd;
}
```