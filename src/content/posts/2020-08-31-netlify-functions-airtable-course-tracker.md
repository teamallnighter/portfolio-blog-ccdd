---
template: blog-post
title: 'Full Stack Jamstack: AirTable Database with Netlify Functions'
slug: /blog/coursetracker
date: '2020-08-31 11:40'
description: >-
  This is from a tutorial from James Q Quick so shout out to him for this
  awesome idea.

  Normally, to have this sort of dynamic content coming from a database you
  would need to know SQL a programming language for databases.
featuredImage: /assets/chris connelly web design calgary.png
---
## Project: Netlify Functions airtable course tracker

##### Build: React, Netlify Serverless Functions, CSS, Node.js and REACT

##### Features: Serverless, airtable database, JAMstack

##### Deployment: Github and Netlify

##### [Check out this video for more](https://blog.chrisconnelly.dev/airtable/netlify/2020/09/03/netlify-airtable.html)

- - -

This is from a[ tutorial](https://youtu.be/VxlbcoJ3nnc) from [James Q Quick](https://github.com/jamesqquick) so shout out to him for this awesome idea.

Normally, to have this sort of dynamic content coming from a database you would need to know SQL a programming language for databases. It would probably take at least ten database tables. This would slow the site down, create some vulnerabilities and take a lot more man hours. 

All we need to do bring in airtable.

```javascript
require('dotenv').config();
var Airtable = require('airtable');
var base = new Airtable({ apiKey: process.env.AIRTABLE_API_KEY }).base(
    process.env.AIRTABLE_BASE_ID
);
const table = base(process.env.AIRTABLE_TABLE_NAME);

module.exports = { table };
```

Create

```javascript
const { table } = require('./airtable');
const formattedReturn = require('./formattedReturn');
module.exports = async (event) => {
    const fields = JSON.parse(event.body);
    try {
        const createdCourse = await table.create([{ fields }]);
        return formattedReturn(200, createdCourse);
    } catch (err) {
        console.error(err);
        return formattedReturn(500, {});
    }
};
```

Delete

```javascript
const { table } = require('./airtable');
const formattedReturn = require('./formattedReturn');
module.exports = async (event) => {
    const { id } = JSON.parse(event.body);
    try {
        const deletedCourse = await table.destroy(id);
        return formattedReturn(200, deletedCourse);
    } catch (err) {
        console.error(err);
        return formattedReturn(500, {});
    }
};
```

Get

```javascript
const { table } = require('./airtable');
const formattedReturn = require('./formattedReturn');
module.exports = async (event) => {
    try {
        const courses = await table.select().firstPage();
        const formattedCourses = courses.map((course) => ({
            id: course.id,
            ...course.fields,
        }));
        return formattedReturn(200, formattedCourses);
    } catch (err) {
        console.error(err);
        return formattedReturn(500, {});
    }
};
```

Update

```javascript
const { table } = require('./airtable');
const formattedReturn = require('./formattedReturn');
module.exports = async (event) => {
    const { id, ...fields } = JSON.parse(event.body);
    try {
        const updatedCourse = await table.update([{ id, fields }]);
        return formattedReturn(200, updatedCourse);
    } catch (err) {
        console.error(err);
        return formattedReturn(500, {});
    }
};
```

![Jamstack web app based on air table](/assets/chris connelly web design calgary.png "The finished app")

![Air Table Database](/assets/fullstack web developer chris connelly.png "The Air Table Database")
