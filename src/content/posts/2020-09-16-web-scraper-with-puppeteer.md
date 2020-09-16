---
template: blog-post
title: "Web Scraper With Puppeteer "
slug: "/puppeteer-scraper "
date: 2020-09-16 02:22
description: Chris Connelly JavaScript Developer Calgary
featuredImage: /assets/puppeteer-scraper-chrisconnellydotdev.png
---
## Project: Puppeteer Scraper

##### Build: Node.js

- - -

This script will go to a web site and open that site on chromium and then take a screen shot of that page. 



![Calgary JavaScript Developer](/assets/example.png "Screenshot from puppeteer")

```javascript
const puppeteer = require('puppeteer');

let truncate = (str, length, truncateStr) => {
    truncateStr = truncateStr || '...';
    length = ~~length;
    return str.length > length ? str.slice(0, length) + truncateStr : str;
};

(async() => {
    const browser = await puppeteer.launch({
        headless: false
    });
    const page = await browser.newPage();

    await page.goto('https://chrisconnelly.dev/', { waitUntil: 'networkidle0' });

    await page.exposeFunction('truncate', (str, length, truncateStr) =>
        truncate(str, length, truncateStr)
    );

    /* Get details from the page */
    let details = await page.evaluate(async() => {

        let getInnerText = selector => {
            return document.querySelector(selector) ? document.querySelector(selector).innerText : false
        }

        return {
            title: await truncate(getInnerText('h1[class="site-title"]'), 5),
            description: getInnerText('p[class="site-description"]'),
            invalid: getInnerText('test[class="test"]')
        }

    });

    debugger;

    // await browser.close();

})();
```