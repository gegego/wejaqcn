---
layout: post
title: "Starting on Heroku"
date: 2018-01-21 16:30:11 +0100
comments: true
categories:
---
Heroku is a cloud platform as a service supporting several programming languages that is used as a web application deployment model. It has been running for 10 years which start from 2007. There are lots of articles to comparing Heroku with other alternative serives, e.g. Amazon Web Sevices, Google App Engine. It maybe not suitable for large bussiness, but Heroku is a good choice of starting your work. Because it offers a real free plan which enough to run a seed web app of different platform and the community is active and helpful which could solve most problems during your work.
<!-- more -->
From this article, I will not introduce the basic thing such as what Heroku is, how to setup or how to deployment which you could find all the things from the [offical site](https://devcenter.heroku.com/). I will introduce my experience of using Heroku service, and talk about some problems during the work.

The first work of mine is this [octopress](http://octopress.org/) blog. Originally, I have deploy one another blog on the github page whose contents is not about technic. However, I really do not want the blog source code and deployment things as pulic things. And Heroku is another choice from the [octopress document](http://octopress.org/docs/deploying/heroku/). I start to know Heroku offers an unlimited free plan and greate documentation. Although I really have no idea about the limits of the free plan, the important thing is the plan could let you define a custom domain. I can not find other services with this option. Honestly, I don't think that there are people coming to read my articles. These blogs mostly are the notes for myself. Following the article, the deployment is quite fast and happy. The CLI tools is simple, however, the drawback or limit is also because of the CLI tools, all the process and work is hiden behind the tools. This limit is not so obvious for the blog. It is just a static web framework, but I think this limitation will affect the advanced development works.

The second work is a django based web application of video contents with a scraper. The internet is a huge database including everything, so the web scraping technology is becoming basements of other work such as machine learning, computer vision, visualization and data analysis. The idea of application is using a python web scraper to collect the video information from some other web sites and insert them to the local database. And the django app lists these videos on the interface and play them for users. One limitation of Heroku is the development enviroments, I use the python to work, so the Heroku app only contains the python enviroments, if you want run a service or process from another language framework such as ruby or java, it seems no way to do that in one app, you need to create another app to deploy the process to the different platform. In some situation, it is a good thing for managing codes and enviroments. But for a large system, it is a big limitation for development and migration. When an app is designed for Heroku, it would take high efforts to transfer it to another cloud plantform. Another problem is that I cannot install the system tools or liberary and control the app or process. There are a lot of addons to offer you the functions but it is still limited and cost more money. In my case, I need a process to run scraper in duration. The easy solution is to use the Scheduler addon, but the setting of timing is very limited. Or we could use 3rd party scheduler lib to develop the service. However, these things are not problems for small app, and it is really fast to develop and deploy your app without any payment. So I think it is ideal platform to convert an idea to a real app and improve
it more and more. And when it becomes big, of course you could contiue on Heroku or move to other big platform like Amazon or Google.

Finally, I will list some tips about development on Heroku.

1. Here are two frameworks of django heroku starting project, I used the second one to start my work. The readme file of the project contains how to deployment and development information.<br />
https://github.com/heroku/python-getting-started<br />
https://github.com/heroku/heroku-django-template

2. Here is a page about setting the postgresql database, and starting project 'python-getting-started' also includes a database example.<br />
https://devcenter.heroku.com/articles/heroku-postgresql

3. Scheduler task creation show below.<br />
https://devcenter.heroku.com/articles/scheduler<br />
https://devcenter.heroku.com/articles/clock-processes-python

4. About 'web scraping with python', it is another big topic. Using [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/) library is a recommended solution, but rendering a dynamic page with javascript sometimes becomes a big chanllege, currently I have not find a good solution for it for my requirements. The details about this topic, the book 'Web Scraping With Python' from Ryan Mitchell is recommended and you can download online.

5. Lastly, I recommend 'https://djangosnippets.org', it is a very useful site about django web app development which includes lots of codes that could be reused.
