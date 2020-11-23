---
template: blog-post
title: Music Player
slug: /javascript/music-player
date: 2020-11-18 20:01
description: Web design Vancouver
featuredImage: /assets/screen-shot-2020-11-18-at-8.02.38-pm.png
---
## Project: Music Player

##### Build: HTML, CSS, Vanilla JS

##### Features: Custom Music Player with spinning record

##### Deployment: Netlify

#### [Live Site](https://ccdd-music-player-ur.netlify.app)

- - -

Just a cool little music player with a spinning record when the music plays. 



![](/assets/web-designer-calgary-alberta.png)

```css
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');

* {
  box-sizing: border-box;
}

body {
background-color: #fff;

  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: 'Lato', sans-serif;
  margin: 0;
}
main{
  padding: 20px;
  border-radius: 20px;
}
.intro{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: 'Lato', sans-serif;

}

.link-container{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: 'Lato', sans-serif;

}

.social-links{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-family: 'Lato', sans-serif;

}

ul{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-family: 'Lato', sans-serif;
}

li{
  list-style: none;
  padding: 20px;
  font-size: 2rem;
}

li:hover{
  text-shadow: 4px 8px 16px 0 grey;
}

a{
  text-decoration: none;
  color: rgb(0, 4, 255);
  text-shadow: 2px 4px 8px grey;
}

a:hover{
  text-shadow: 4px 8px 16px 0 grey;
}

.music-container {
  background-color: rgb(0, 0, 0);
  border-radius: 15px;
  box-shadow: 4px 8px 16px 0 rgba(252, 169, 169, 0.6);
  display: flex;
  padding: 20px 30px;
  position: relative;
  margin: 100px 0;
  z-index: 10;
}

.img-container {
  position: relative;
  width: 110px;
}

.img-container::after {
  content: '';
  background-color: #fff;
  border-radius: 50%;
  position: absolute;
  bottom: 100%;
  left: 50%;
  width: 20px;
  height: 20px;
  transform: translate(-50%, 50%);
}

.img-container img {
  border-radius: 50%;
  object-fit: cover;
  height: 110px;
  width: inherit;
  position: absolute;
  bottom: 0;
  left: 0;
  animation: rotate 3s linear infinite;

  animation-play-state: paused;
}

.music-container.play .img-container img {
  animation-play-state: running;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

.navigation {
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1;
}

.action-btn {
  background-color: rgb(0, 0, 0);
  border: 0;
  color: #d619d6;
  font-size: 20px;
  cursor: pointer;
  padding: 10px;
  margin: 0 20px;
}

.action-btn.action-btn-big {
  color: #a30ecc;
  font-size: 30px;
}

.action-btn:focus {
  outline: 0;
}

.music-info {
  background-color: rgba(0, 0, 0, 0.377);
  border-radius: 15px 15px 0 0;
  position: absolute;
  top: 0;
  left: 20px;
  width: calc(100% - 40px);
  padding: 10px 10px 10px 150px;
  opacity: 0;
  transform: translateY(0%);
  transition: transform 0.3s ease-in, opacity 0.3s ease-in;
  z-index: 0;
}

.music-container.play .music-info {
  opacity: 1;
  transform: translateY(-100%);
}

.music-info h4 {
  margin: 0;
}

.progress-container {
  background: #fff;
  border-radius: 5px;
  cursor: pointer;
  margin: 10px 0;
  height: 4px;
  width: 100%;
}

.progress {
  background-color: #fe8daa;
  border-radius: 5px;
  height: 100%;
  width: 0%;
  transition: width 0.1s linear;
}
```

```javascript
const musicContainer = document.getElementById('music-container');
const playBtn = document.getElementById('play');
const prevBtn = document.getElementById('prev');
const nextBtn = document.getElementById('next');

const audio = document.getElementById('audio');
const progress = document.getElementById('progress');
const progressContainer = document.getElementById('progress-container');
const title = document.getElementById('title');
const cover = document.getElementById('cover');

// Song titles
const songs = ['smokin', 'smashy', 'say', 'lizzo', 'pbj'];

// Keep track of song
let songIndex = 4;

// Initially load song details into DOM
loadSong(songs[songIndex]);

// Update song details
function loadSong(song) {
  title.innerText = song;
  audio.src = `music/${song}.mp3`;
  cover.src = `images/${song}.png`;
}

// Play song
function playSong() {
  musicContainer.classList.add('play');
  playBtn.querySelector('i.fas').classList.remove('fa-play');
  playBtn.querySelector('i.fas').classList.add('fa-pause');

  audio.play();
}

// Pause song
function pauseSong() {
  musicContainer.classList.remove('play');
  playBtn.querySelector('i.fas').classList.add('fa-play');
  playBtn.querySelector('i.fas').classList.remove('fa-pause');

  audio.pause();
}

// Previous song
function prevSong() {
  songIndex--;

  if (songIndex < 0) {
    songIndex = songs.length - 1;
  }

  loadSong(songs[songIndex]);

  playSong();
}

// Next song
function nextSong() {
  songIndex++;

  if (songIndex > songs.length - 1) {
    songIndex = 0;
  }

  loadSong(songs[songIndex]);

  playSong();
}

// Update progress bar
function updateProgress(e) {
  const { duration, currentTime } = e.srcElement;
  const progressPercent = (currentTime / duration) * 100;
  progress.style.width = `${progressPercent}%`;
}

// Set progress bar
function setProgress(e) {
  const width = this.clientWidth;
  const clickX = e.offsetX;
  const duration = audio.duration;

  audio.currentTime = (clickX / width) * duration;
}

// Event listeners
playBtn.addEventListener('click', () => {
  const isPlaying = musicContainer.classList.contains('play');

  if (isPlaying) {
    pauseSong();
  } else {
    playSong();
  }
});

// Change song
prevBtn.addEventListener('click', prevSong);
nextBtn.addEventListener('click', nextSong);

// Time/song update
audio.addEventListener('timeupdate', updateProgress);

// Click on progress bar
progressContainer.addEventListener('click', setProgress);

// Song ends
audio.addEventListener('ended', nextSong);
```