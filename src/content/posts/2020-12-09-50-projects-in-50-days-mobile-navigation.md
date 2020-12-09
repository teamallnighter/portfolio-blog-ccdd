---
template: blog-post
title: "50 Projects In 50 Days:  Mobile Navigation"
slug: /javascript/mobile-nav
date: 2020-12-16 20:07
description: A mobile navigation with slide outs that are delayed
featuredImage: /assets/screen-shot-2020-12-08-at-7.58.54-pm.png
---
## Project: Random Choice Picker

##### Build: HTML, SASS, Vanilla JS

##### Features: pick a random thing from an array provided by the user.

##### Deployment: Netlify

#### [Live Site](https://50-projects-in-50-days.netlify.app/random-choice-picker)

- - -

This is my favourite app so far! It was a lot of fun. The user inputs their choices separated by commas. The app will then pick a random choice.

```javascript
const tagsEl = document.getElementById('tags')
const textarea = document.getElementById('textarea')

textarea.focus()

textarea.addEventListener('keyup', (e) => {
    createTags(e.target.value)

    if(e.key === 'Enter') {
        setTimeout(() => {
            e.target.value = ''
        }, 10)

        randomSelect()
    }
})

function createTags(input) {
    const tags = input.split(',').filter(tag => tag.trim() !== '').map(tag => tag.trim())
    
    tagsEl.innerHTML = ''

    tags.forEach(tag => {
        const tagEl = document.createElement('span')
        tagEl.classList.add('tag')
        tagEl.innerText = tag
        tagsEl.appendChild(tagEl)
    })
}

function randomSelect() {
    const times = 30

    const interval = setInterval(() => {
        const randomTag = pickRandomTag()

        highlightTag(randomTag)

        setTimeout(() => {
            unHighlightTag(randomTag)
        }, 100)
    }, 100);

    setTimeout(() => {
        clearInterval(interval)

        setTimeout(() => {
            const randomTag = pickRandomTag()

            highlightTag(randomTag)
        }, 100)

    }, times * 100)
}

function pickRandomTag() {
    const tags = document.querySelectorAll('.tag')
    return tags[Math.floor(Math.random() * tags.length)]
}

function highlightTag(tag) {
    tag.classList.add('highlight')
}

function unHighlightTag(tag) {
    tag.classList.remove('highlight')
}
```