---
template: blog-post
title: Vyyl Blood Drip Parking Page
slug: /vyyl-blood
date: 2020-09-09 07:49
description: Chris Connelly Calgary Web Designer
featuredImage: /assets/screen-shot-2020-09-09-at-7.47.12-am.png
---
While we finish building out the page, I created this awesome blood drip landing page that takes newsletter sign ups. 



check it out: <https://vyyl.ca>



```html
<main class="off-canvas__main bg shadow-sm main-index">
            <section class="bg-cover bg-center bg-no-repeat padding-y-xxl">
               <div class="container max-width-adaptive-sm">
                  <div class="bg bg-opacity-60% padding-md padding-xxl@md flex flex-column">
                     <div class="text-component margin-bottom-sm home-container">
                      <link href="https://fonts.googleapis.com/css?family=Raleway:300,500,700,900" rel="stylesheet">

                      <svg xmlns="http://www.w3.org/2000/svg" version="1.1" style="width: 0;height: 0;">
                        <defs>
                          <filter id="goo">
                            <feGaussianBlur in="SourceGraphic" stdDeviation="4" result="blur" />
                            <feColorMatrix in="blur" mode="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -7" result="goo" />
                            <feBlend in="SourceGraphic" in2="goo" />
                          </filter>
                        </defs>
                      </svg>
                      
                      <h1 class="title">
                        VYYL
                        <span class="drop"></span>
                        <span class="drop"></span>
                        <span class="drop"></span>
                        <span class="drop"></span>
                        <span class="drop"></span>
                      </h1>
                     </div>
                     <div class="flex flex-wrap items-center gap-sm home-container-btns">
                       
                        <!--<a href="/player.html" target="popup" onclick="window.open('/player.html','popup','width=500,height=800'); return false;" class="glow-on-hover"><button class="glow-on-hover" >AUDIO</button></a>-->
                        <!--<a href="/visual.html"><button class="glow-on-hover" >VISUAL</button></a>
                        -->
                        <button class="deactivated">COMING SOON</button>
                        <button class="glow-on-hover" aria-controls="modal-form">Get Updates</button>
                     </div>
                  </div>
               </div>
            </section>
         </main>
<div class="modal modal--animate-scale flex flex-center bg-contrast-higher bg-opacity-90% padding-md js-modal" id="modal-form">
  <div class="modal__content width-100% max-width-xs padding-md bg radius-md shadow-md" role="alertdialog" aria-labelledby="modal-form-title" aria-describedby="modal-form-description">
    <div class="text-component margin-bottom-md">
      <h3 id="modal-form-title">JOIN THE VYYL NEWSLETTER</h3>
      <p id="modal-form-description">Get updates on our new website, giveaways, show announcements and more</p>
    </div>

    <form name="landing-newsletter" method="POST" data-netlify="true" class="margin-bottom-sm" >
      <div class="flex flex-column flex-row@xs gap-xxxs">
        <input name="email" aria-label="Email" class="form-control flex-grow" type="email" placeholder="Email">
        <button class="btn btn--primary">Subscribe</button>
      </div>
    </form>

    <div class="text-component">
      <p class="text-xs color-contrast-medium">We will never sell your information your <a href="/privacy.html" class="color-contrast-high">privacy is important</a> to us</p>
    </div>
  </div>

  <button class="reset modal__close-btn modal__close-btn--outer  js-modal__close js-tab-focus">
    <svg class="icon icon--sm" viewBox="0 0 24 24">
      <title>Close modal window</title>
      <g fill="none" stroke="currentColor" stroke-miterlimit="10" stroke-width="2">
        <line x1="3" y1="3" x2="21" y2="21" />
        <line x1="21" y1="3" x2="3" y2="21" />
      </g>
    </svg>
  </button>
</div>
```



The CSS



```sass
.glow-on-hover {
    width: 220px;
    height: 50px;
    border: none;
    outline: none;
    color: #fff;
    background: #111;
    cursor: pointer;
    position: relative;
    z-index: 0;
    border-radius: 10px;
}

.glow-on-hover:before {
    content: '';
    background: linear-gradient(45deg, #ff0000, #ee0707, #d30b0b, #932911, #ffa200, #ff002f, #ff2600, #960709, #ff0000);
    position: absolute;
    top: -2px;
    left:-2px;
    background-size: 400%;
    z-index: -1;
    filter: blur(5px);
    width: calc(100% + 4px);
    height: calc(100% + 4px);
    animation: glowing 20s linear infinite;
    opacity: 0;
    transition: opacity .3s ease-in-out;
    border-radius: 10px;
}

.glow-on-hover:active {
    color: rgb(26, 24, 24)
}

.glow-on-hover:active:after {
    background: transparent;
}

.glow-on-hover:hover:before {
    opacity: 1;
}

.glow-on-hover:after {
    z-index: -1;
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgb(23, 22, 22);
    left: 0;
    top: 0;
    border-radius: 10px;
}

@keyframes glowing {
    0% { background-position: 0 0; }
    50% { background-position: 400% 0; }
    100% { background-position: 0 0; }
}

.title {
    font-weight: 900;
    font-size: 20vw;
    margin: 0;
    filter: url(#goo);
    position: relative;
    letter-spacing: -.12em;
    color:#8A0303;
    text-transform: uppercase;
  }
  
  .drop {
    width: .1em; height: .1em;
    border-radius: 0 100% 100% 100%;
    background-color: currentColor;
    position: absolute;
    top: 72%;
    animation: drop 3s infinite both;
  
    &:nth-child(1) {
      left: 14%;
    }
  
    &:nth-child(2) {
      left: 39%;
      animation-delay: -.4s;
    }
  
    &:nth-child(3) {
      left: 55%;
      animation-delay: -1.5s;
    }
  
    &:nth-child(4) {
      left: 82%;
      animation-delay: -.8s;
    }
  
    &:nth-child(5) {
      left: 95.5%;
      animation-delay: -1.3s;
    }
  }
  
  @keyframes drop {
    0% {
      transform: translateY(0) scaleX(.85) rotate(45deg);
      animation-timing-function: ease-out;
    }
    60% {
      transform: translateY(120%) scaleX(.85) rotate(45deg);
      animation-timing-function: ease-in;
    }
    80%, 100% {
      transform: translateY(60vh) scaleX(.85) rotate(45deg);
    }
  }
```