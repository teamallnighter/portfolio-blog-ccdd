---
template: blog-post
title: "50 Projects In 50 Days: Progress Steps"
slug: /javascript/progress-steps
date: 2020-12-05 08:21
description: Web Design Calgary As a part of a course I am taking I built a
  progress step app. This simply shows which step you are on and would work
  great with a multi page form.
featuredImage: /assets/2ps.png
---
## Project: Progress Steps

##### Build: HTML, SASS, Vanilla JS

##### Features: Progress steps that change the buttons.

##### Deployment: Netlify

#### [Live Site](https://50-projects-in-50-days.netlify.app/progresssteps/)

- - -

As a part of a course I am taking I built a progress step app. This simply shows which step you are on and would work great with a multi page form.



```javascript
const progress = document.getElementById('progress')
const prev = document.getElementById('prev')
const next = document.getElementById('next')
const circles = document.querySelectorAll('.circle')

let currentActive = 1

next.addEventListener('click', () => {
    currentActive++

    if(currentActive > circles.length) {
        currentActive = circles.length
    }

    update()
})

prev.addEventListener('click', () => {
    currentActive--

    if(currentActive < 1) {
        currentActive = 1
    }

    update()
})

function update() {
    circles.forEach((circle, idx) => {
        if(idx < currentActive) {
            circle.classList.add('active')
        } else {
            circle.classList.remove('active')
        }
    })

    const actives = document.querySelectorAll('.active')

    progress.style.width = (actives.length - 1) / (circles.length - 1) * 100 + '%'

    if(currentActive === 1) {
        prev.disabled = true
    } else if(currentActive === circles.length) {
        next.disabled = true
    } else {
        prev.disabled = false
        next.disabled = false
    }
}
```