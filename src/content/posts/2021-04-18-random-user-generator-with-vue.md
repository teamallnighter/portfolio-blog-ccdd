---
template: blog-post
title: Random User Generator With VUE
slug: /vue/random-user
date: 2021-04-18 07:29
description: Vue Js Developer Calgary
featuredImage: /assets/screen-shot-2021-04-18-at-7.30.03-am.png
---
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>CodePen - Vue.js Random User Generator</title>
    <link rel="stylesheet" href="./style.css">

</head>

<body>
    <!-- partial:index.partial.html -->
    <div id="app">
        <img v-bind:src="picture" :alt="`${firstName} ${lastName}`" :class="gender" />
        <h1>{{firstName}} {{lastName}}</h1>
        <h3>Email: {{email}}</h3>
        <button :class="gender" @click="getUser()">Get Random User</button>
    </div>
    <!-- partial -->
    <script src='https://unpkg.com/vue@3.0.5'></script>
    <script src="./script.js"></script>

</body>

</html>
```


---


```javascript
const app = Vue.createApp({
    data() {
        return {
            firstName: 'John',
            lastName: 'Doe',
            email: 'john@gmail.com',
            gender: 'male',
            picture: 'https://randomuser.me/api/portraits/men/10.jpg',
        }
    },
    methods: {
        async getUser() {
            const res = await fetch('https://randomuser.me/api')
            const { results } = await res.json()

            // console.log(results)

            this.firstName = results[0].name.first
            this.lastName = results[0].name.last
            this.email = results[0].email
            this.gender = results[0].gender
            this.picture = results[0].picture.large
        },
    },
})

app.mount('#app')
```