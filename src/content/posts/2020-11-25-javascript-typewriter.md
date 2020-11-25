---
template: blog-post
title: JavaScript TypeWriter
slug: javascript/type-writer-js
date: 2020-11-25 07:36
description: Web design Calgary | Web Design Alberta | Chris Connelly |
  JavaScript Developer.
featuredImage: /assets/screen-shot-2020-11-25-at-7.39.07-am.png
---


## TypeWriter.js

##### Build: HTML | CSS | JavaScript

##### Features: Types out content with random timing between keystrokes

##### Deployment: Netlify

#### [Check it out](https://type-writer-js-ccdd.netlify.app/example3-typewriter/)

#### Shout out to [mehaase](https://github.com/mehaase) on Github for this one!

- - -

This was a fun little project. The code is very straight forward:



```javascript
<!DOCTYPE html>
<html>
    <head>
        <title>Example 3: Typewriter</title>
        <link rel="stylesheet" href="../css/normalize.css"/>
        <link rel="stylesheet" href="../css/skeleton.css"/>
        <link href='//fonts.googleapis.com/css?family=Special+Elite' rel='stylesheet' type='text/css'>
        <style>
            body {
                background-color:white;
                color: black;
                font-family: 'Special Elite', cursive;
            }
            #typewriter {
                white-space: pre;
            }
        </style>
        <script src="//code.jquery.com/jquery-1.10.1.min.js"></script>
        <script src="../typewriter.js"></script>
        <script src="./animate.js"></script>
        <script src="./howler.min.js"></script>
    </head>
    <body>
        <main>
            <section>
                <article>
                    <div class="container page-wrapper">
                        <button id='playButton'>Play <svg height="15" aria-hidden="true" focusable="false" data-prefix="fal" data-icon="play-circle" class="svg-inline--fa fa-play-circle fa-w-16" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="currentColor" d="M256 504c137 0 248-111 248-248S393 8 256 8 8 119 8 256s111 248 248 248zM40 256c0-118.7 96.1-216 216-216 118.7 0 216 96.1 216 216 0 118.7-96.1 216-216 216-118.7 0-216-96.1-216-216zm331.7-18l-176-107c-15.8-8.8-35.7 2.5-35.7 21v208c0 18.4 19.8 29.8 35.7 21l176-101c16.4-9.1 16.4-32.8 0-42zM192 335.8V176.9c0-4.7 5.1-7.6 9.1-5.1l134.5 81.7c3.9 2.4 3.8 8.1-.1 10.3L201 341c-4 2.3-9-.6-9-5.2z"></path></svg></button>
                    <div class="container poem-wrapper">
                        <p id="typewriter"></p>
                    </div>
                </div>
            </article>
        </section>
    </main>
        <script>
        // Audio files are royalty-free from http://www.soundjay.com/typewriter-sounds.html.
        var carriageReturnSound = new Howl({
            src: ['./typewriter-carriage-return.mp3']
        });
        var keystrokeSound = new Howl({
            src: ['./typewriter-keystroke.mp3']
        });
        var currentSound = null;

        function playSound (character) {
            var nextSound = null;
            carriageReturnSound.pause();
            keystrokeSound.pause();

            if (character == "\n") {
                carriageReturnSound.currentTime = 0;
                nextSound = carriageReturnSound;
            } else if (character != " ") {
                keystrokeSound.currentTime = 0;
                nextSound = keystrokeSound;
            }

            if (nextSound != null) {
                if (currentSound != null) {
                    currentSound.stop();
                }
                currentSound = nextSound;
                currentSound.play();
            }
        }

        $('#playButton').click(function () {
            var typewriter = new Typewriter($("#typewriter"));
            typewriter.setCaret("");
            typewriter.setCaretPeriod(0);
            typewriter.setDelay(200, 50);
            typewriter.setCharacterCallback(playSound);
            animate(typewriter);
        });
        </script>
    </body>
</html>

```