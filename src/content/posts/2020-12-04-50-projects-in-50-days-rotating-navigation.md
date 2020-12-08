---
template: blog-post
title: "50 Projects In 50 Days: Rotating Navigation"
slug: /javascript/rotating-nav
date: 2020-12-06 08:33
description: Web Design Edmonton |Continuing on with my 50 projects in 50 days
  course. We built a rotating navigation. This one looks REALLY great. When you
  click the hamburger menu, the page tilts on a 45 degree angle exposing the
  menu.
featuredImage: /assets/3rn.png
---
## Project: Rotating Nav

##### Build: HTML, SASS, Vanilla JS

##### Features: A navigation that rotates the main content

##### Deployment: Netlify

#### [Live Site](https://50-projects-in-50-days.netlify.app/rotating-nav/)

- - -

Continuing on with my 50 projects in 50 days course. We built a rotating navigation. This one looks REALLY great. When you click the hamburger menu, the page tilts on a 45 degree angle exposing the menu. 



```javascript
const open = document.getElementById('open')
const close = document.getElementById('close')
const container = document.querySelector('.container')

open.addEventListener('click', () => container.classList.add('show-nav'))

close.addEventListener('click', () => container.classList.remove('show-nav'))
```