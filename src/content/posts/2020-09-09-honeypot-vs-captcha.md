---
template: blog-post
title: Honeypot vs Captcha
slug: /honeypot
date: 2020-09-08 21:32
description: Calgary Web Developer Chris Connelly. This is a honeypot spam
  filter. Its a form field that a human can'y see but a bot would fill out
featuredImage: /assets/carbon.png
---
This is a simple spam filtering technique where we build a hidden form field that humans can't see. A bot would fill out the field so that would be sent to the spam filter. 

```html
<!--this tell netlify we are using this form and what field is hidden-->
<form class="form-template-v3" method="POST" netlify-honeypot="bot-field" data-netlify="true">
 
  <!--This is the field itself-->
   <p class="hidden" style="display:none">
      <label>Don’t fill this out if you're human: <input name="bot-field" /></label>
   </p>
  
```

Thats all you need!

![Honey Pot Form Results - Chris Connelly - Calgary Web Developer](/assets/screen-shot-2020-09-08-at-9.29.53-pm.png "As you can see the field doesn't show up on the form.")