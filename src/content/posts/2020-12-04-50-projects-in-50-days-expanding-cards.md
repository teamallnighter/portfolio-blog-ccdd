---
template: blog-post
title: "50 Projects in 50 Days: Expanding Cards"
slug: /javascript/expanding-cards
date: 2020-12-04 08:19
description: JavaScript Developer Calgary | I recently signed up for a course
  where we do 50 javaScript projects in 50 days. Today I worked on these
  expanding cards. I think they would look great on just about any web site and
  super easy to set up.
featuredImage: /assets/1ec.png
---
```javascript
//Select all panel classes
const panels = document.querySelectorAll('.panel')

//Loop through the panels
panels.forEach(panel => {
    panel.addEventListener('click', () => {
        removeActiveClasses()
        panel.classList.add('active')
    })
})

function removeActiveClasses() {
    panels.forEach(panel => {
        panel.classList.remove('active')
    })
}
```

## Project: Expanding Cards

##### Build: HTML, SASS, Vanilla JS

##### Features: Awesome Looking Expanding Cards

##### Deployment: Netlify

#### [Live Site](https://50-projects-in-50-days.netlify.app/expandingcards/)

- - -

I recently signed up for a course where we do 50 javaScript projects in 50 days. 

Today I worked on these expanding cards. I think they would look great on just about any web site and super easy to set up.