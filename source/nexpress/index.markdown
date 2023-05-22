---
layout: page
title: "NexPress"
date: 2018-03-18 16:50
comments: true
sharing: true
footer: true
---
Reference:[https://www.kodak.com/us/en/print/Products/Printers_Presses/Nexpress_Platform/default.htm](https://www.kodak.com/us/en/print/Products/Printers_Presses/Nexpress_Platform/default.htm)

This project is a management system to the nexpress device. The motivation of this project is that the orignal mangement system is old(about used from 2003) which is develped based on java applet gui and c++ device sdk. There are issues when java update every time and it also couldn't meet the new requirements for the mobile devices.

So we start to design and develop new system with latest B/S framework. The frontend is developped on AngularJS and Bootstrap UI. And backend system create a [bottle](https://bottlepy.org/docs/dev/) web server and a websocket server ([gevent](http://www.gevent.org/)). Bottle server is router from url to html page and web socket creation. The web socket server waiting the message content from frontend, call the engine service and return the feedback. And json used as the data type of web socket connection.

{% img /images/nexpress.png %}

Shown as the figure, the frontend create a websocket connection when openning. And in funtion page, sending message with parameters like "evt=method" to server, the server calls the related engine method and get json feedback. [Here](https://github.com/gegego/WorkConnect) is source code of a prototype webapp example of similar framework design.

Firstly the project is just for prototyping to the customers of nexpress. However some customers likes the user interaction of monitoring of job status and sending jobs with mobile device like IPAD or moblie phone. So we can contiue to doing the work of more functions.

The chanllege of the project is the user interaction of web is toally different with old java desktop app, we need to design the new UI to satisfy the requirments. And it is the first big business modern web system project for me. And I am very glad to learn the new things like angularjs and python.
