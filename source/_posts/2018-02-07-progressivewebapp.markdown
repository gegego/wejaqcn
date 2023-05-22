---
layout: post
title: "Create Progressive Web App"
date: 2018-02-07 22:04:18 +0100
comments: true
categories:
---
Progressive Web Application (PWA) is designed for mobile, starting from Google for Android Chrome and Chrome OS from 2015, and it is not only a shortcuts of url, but also it takes web application benefits and add advanced features to give the experience same as the first-class naive app.
<!-- more -->

To transfer your web app or site to a progressive web application is not complicated. [Here](https://developers.google.com/web/progressive-web-apps/checklist) is a checklist of PWA. Simply, it only needs some steps.

1. Designing the layout of web app for mobile resolution.<br />
2. Installing ssl certificates on the web server, makes the web app under https.<br />
3. Create configration metadata for Add to Home Screen.<br />
4. Open web app on mobile browser (Chrome, Firefox, Opera), Add to Home Screen.<br />

For designing layout of Mobile, we could create `@media (min-width:1200px)` nodes in css file to define different css layout for different page size. And of course, we could design specific UI template for Mobile, and at backend, check the browser type from request information, and link to the url for mobile or desktop version.

There are lots of solutions of installing ssl certificates of web server, and it includes some free solutions, e.g. [letsencrypt](https://letsencrypt.org/). Use [certbot](https://github.com/certbot/certbot) tools to install the certificates with only some commands.

The easist way to set the metadata is only set `<meta name="mobile-web-app-capable" content="yes">` on the main html page. But it is only for Chrome. Other browser e.g. firefox need to define a manifest file `manifest.json` like, reference is [here](https://developers.google.com/web/fundamentals/native-hardware/fullscreen/).
```
{
  "short_name": "Kinlan's Amaze App",
  "name": "Kinlan's Amazing Application ++",
  "icons": [
    {
      "src": "launcher-icon-4x.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ],
  "start_url": "/index.html",
  "display": "standalone",
  "orientation": "landscape"
}
```
After these steps, we could run our web app like a first-class naive app. And if we want to more advanced function, we need to work with the webAPI from different browser offering, moreover it is even possible to create an offline web app by using [service workers](https://developers.google.com/web/updates/2016/06/2-cookie-handoff). [Here](https://developers.google.com/web/) is all the things about web app from GOOGLE
