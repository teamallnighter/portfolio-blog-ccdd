---
template: blog-post
title: "Chris Learns Deno: NASA Control Centre"
slug: /deno/nasa-control
date: 2020-09-18 00:39
description: "Chris Connelly a JavaScript Developer Calgary Alberta "
featuredImage: /assets/screen-shot-2020-09-18-at-12.40.28-am.png
---
##### Build: Deno

##### Features: An API that pulls data from SPACEX's API on missions

#### [GITHUB](https://github.com/teamallnighter/chris-learns-deno/tree/master/nasa)

- - -

This was a super fun app to build. This app takes data and displays it from SAPCEX and NASA on missions

![JavaScript Developer Calgary](/assets/screen-shot-2020-09-18-at-12.40.28-am.png "The Mission Control Center")

It also display this data using an API call. 

![Web Design Calgary](/assets/screen-shot-2020-09-18-at-12.40.56-am.png "The Postman response ")



![Web Developer Calgary](/assets/screen-shot-2020-09-18-at-12.40.22-am.png "The Data on the browser")



```
import { Application } from "https://deno.land/x/oak/mod.ts";

const app = new Application();
const Port = 8000;

app.use(( ctx ) => {
    ctx.response.body = 'HELLO WORLD';
});

if (import.meta.main) {
    app.listen({
        port: Port
        });
}
```