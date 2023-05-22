---
layout: page
title: "Smart Messager"
date: 2018-03-17 22:52
comments: true
sharing: true
footer: true
---
Reference: [https://www.necplatforms.co.jp/solution/smartmessenger/](https://www.necplatforms.co.jp/solution/smartmessenger/)

Smart Messager is a voice message deliver system. Front-end system is created by ASP.Net and C# which visualize the status of message calling, sending message and other management functions. Back-end system includes a calling controlling server, SIP proxy server and other modules. Both sides communicates by WCF service.

{% img /images/smartmessage.png %}

Shown as the figure, the client includes two types, web and phone. The server includes a phone calling management system which setup a SIP proxy server monitoring a port to waiting SIP request from client phones, and then routes the phone requests to the related functions by a script. Meanwhile server also includes some WCF services which offers functions for web clients. From another side, the system sending voice messages to the target phones through PBX by SIP/RTP. And update the status of calling to the data files(xml files).

The chanllege work of the project is to send message to many target phones(100+ phones) at mean time and make sure that every message send and receive sucessfully, and then update the real-time status of calling by AJAX on the web client. The whole system design is also chanllegable, the requirements change a lot during the development, so the design need big flexibility to expand new requirements.

For me, this project is a very important, it give me a chance to implement a production application with some intresting devices: ip-phone, voip router and pbx. And I almost take part in every part of the development and learn lots about programming with mixed languages with C#, C++/cli, naitve C++ and some c/c++ opensource library, although we meet lots of compiling and linking problems.

{% img /images/1.png %}
The photo was shoted when we finished all the work in the lab in Tokyo.
