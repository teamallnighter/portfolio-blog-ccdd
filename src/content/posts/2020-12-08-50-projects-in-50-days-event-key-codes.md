---
template: blog-post
title: "50 Projects In 50 Days: event Key Codes"
slug: /javascript/event-key-codes
date: 2020-12-12 22:32
description: Web Design Calgary | In this project we built an app that
  recognizes and displays key strokes from the user.
---
## Project: Event Key Codes

##### Build: HTML, SASS, Vanilla JS

##### Features: Progress steps that change the buttons.

##### Deployment: Netlify

#### [Live Site](http://127.0.0.1:5501/event-key-codes/)

- - -

In this project we built an app that recognizes and displays key strokes from the user.





```javascript
const insert = document.getElementById('insert')

window.addEventListener('keydown', (event) => {
  insert.innerHTML = `
  <div class="key">
  ${event.key === ' ' ? 'Space' : event.key} 
  <small>event.key</small>
</div>
<div class="key">
  ${event.keyCode}
  <small>event.keyCode</small>
</div>
<div class="key">
  ${event.code}
  <small>event.code</small>
</div>
  `
})
```