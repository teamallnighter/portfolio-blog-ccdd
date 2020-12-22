---
template: blog-post
title: Glassmorphism
slug: /css/glassmorphism
date: 2020-12-22 09:12
description: CSS and SASS developer Calgary
featuredImage: /assets/screen-shot-2020-12-22-at-9.12.52-am.png
---
This is a fun way of using glassmorphism in HTML CSS and javaScript. 

```html
<!DOCTYPE html>
<html lang="en" >
<head>
  <meta charset="UTF-8">
  <title>CodePen - Glassmorphism Example</title>
  <link rel="stylesheet" href="style.css">

</head>
<body>
<!-- partial:index.partial.html -->
<img src="abstract.jpg" alt="abstract background">
    <div class="circle"></div>

    <div class="container" id="glass">
        <h2 class="seq">chrisConnellyDotDev</h2>
        <p class="seq">User friendly ≠ Cookie Cutter</p>
    </div>

    <h1>Glassmorphism</h1>
<!-- partial -->
  <script src='https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/gsap.min.js'></script><script  src="./script.js"></script>

</body>
</html>
```



```css
body {
  background: #c8dce7;
  color: black;
  font-family: 'Poppins';
  margin: 0;
  padding: 14em 14em 14em 20em;
}

img {
  position: absolute;
  z-index: -2;
  height: 100vh;
  top: 0;
  left: 0;
}

.container {
  display: inline-block;
  background: rgba(255, 255, 255, 0.2);
  padding: 3em;
  border-radius: 3em;
  position: relative;
  z-index: 1;
  backdrop-filter: blur(40px);
  border: solid 2px transparent;
  background-clip: padding-box;
  box-shadow: 10px 10px 10px rgba(46, 54, 68, 0.03);
}
.container h2 {
  font-size: 1.7em;
}
.container h1, .container h2 {
  margin: 0;
}
.container p {
  margin: 0;
}

h1 {
  font-size: 4em;
  clip-path: inset(0 0 0 0);
}
```



```javascript
const glass = document.getElementById('glass');

        const tl = gsap.timeline({defaults: {ease: "power2.inOut", duration: 1.5}})

        tl.from('img', { x: '-10%', opacity: 0})
          .from('.container', {opacity: 0, delay: .5, duration: 1}, "-=1.5")
          .from('.container', {x: '-20%', backdropFilter: 'blur(0px)'})
          .from('.seq', { y: -30, opacity: 0, stagger: .2, duration: .5}, "-=.5")
          .from('h1', { y: 20, clipPath: 'inset(0 0 100% 0)'}, "-=.8")
```