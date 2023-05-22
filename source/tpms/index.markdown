---
layout: page
title: "Tire Pressure Monitoring System"
date: 2018-03-19 12:44
comments: true
sharing: true
footer: true
---
TPMS is final thesis of my Bachlor. We design and implement the whole software of the system by assembly language on Renesas r8c mcu.

{% img /images/cartpms.png %}

As shown as the figure, the system includes 4 tire messurment units and one center receiver unit.

My work is mainly focus on the software of receiver on Renesas mcu and sender unit on GE NPXII chip. And designing assembly software sturctures sometimes is easier than high level language. It is funtional based framework, we design the functions as workflows from top to down, then implement every funtion block of the workflow. The features includes wireless communication, uart communication, manchester decode and so on.

[**Documentation**](/images/tpms.pdf) is writen in Chinese, it includes design and implement of sender unit, receiver unit is writen by another group mate, although we did this project together. [**SRC**](/images/tpms_src.txt) is source code of the prototype of the receiver unit, and comments are mostly in Chinese, so it could not shown.

For me, this project give me a chance first to touch with a real business project. We work with a local company and I learn lots of low level software development. And design and impelment of features like wireless communication is also a big chanllege for me.
