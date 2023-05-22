---
layout: page
title: "MA4000"
date: 2018-03-17 17:21
comments: true
sharing: true
footer: true
---
Reference: [https://www.nec-enterprise.com/products/MA4000-System-Management-98](https://www.nec-enterprise.com/products/MA4000-System-Management-98)

MA4000 is to create bussiness model of PBX data to replace the PBX command system. The old command system is too complicate to learn and operate. E.g. when someone want to register a specific kind of phone in the PBX, he should input 5 or more commands to the pbx system with lots of parameters following the manual book(1000 pages). This group of commands are nothing related to the real meanings of the phone. Command is close to a bash style. MA4000 system create the real bussiness type and understandable UI of the phone to let user easliy to manage the data of PBX which hides the real data and commands. E.g. instead of a group of hardcore commands, the system could visualize and operate a real phone model with its parameters from the user interaction.


{% img /images/ma4000.png %}

Shown as figure, the system is designed as a traditional 3 layers sturctures. View layer includes UI based on ASP.net which visualize the data and user interation of functions. And the funcion workflow and bussiness defination is implemented in business layer. The final data layer mainly focus on DB operation and PBX command message communication with PBXEngineSDK which is developed as another project.

The source code is about 50 mb large under zip compress, more than 100 mouldes defined, and includes a large database with 5 mb size package of sql files. The duration of the project development is longer than 10 years until now.

I thought it is an old design and becomes complicated when it turns large without flexibility as modern framework design. But it includes everything about business system development on .Net framework on Windows server. The chanllege work of the project is how to design the business object to the PBX data, and design the user interaction of the features.
