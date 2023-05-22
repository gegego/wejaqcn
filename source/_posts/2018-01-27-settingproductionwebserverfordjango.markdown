---
layout: post
title: "Setup of Production Server with nginx and uwsgi"
date: 2018-01-27 15:16:49 +0100
comments: true
categories:
---
These two days, I trid to create a production web server with nginx and uwsgi for django app on a VPS from vultr.com. With the help from some [atircles](http://uwsgi-docs.readthedocs.io/en/latest/tutorials/Django_and_nginx.html) from internet, I learn lots of things and finished the work finally.
<!-- more -->
### Configuration
The depolyment work mainly contains some steps.

1, Installing python and pip tools and create vitural enviroments for your projects by virtualenv.

2, Transfering the project deployment space to the VPS, mostly through git or other similar tools.

3, Installing python dependency packages by requirements.txt with command `pip install -r requirements.txt`, then installing the database and other dependency tools for the project.

4, Initializing the django app like command migrate, collectstatic and so on. Then run the server from django by `python manage.py runserver 0.0.0.0:8000`, it should be working.

Go to here, I did not meet any problems, everything is fine.

5, Installing [uwsgi](http://uwsgi-docs.readthedocs.io/en/latest/index.html), simply, using `uwsgi --http: 8000 --module=project.wsgi` to run your project, it wokred like last step. Then, create an config file named `project.ini` such as [example](http://uwsgi-docs.readthedocs.io/en/latest/Configuration.html) to a port or a socket file, and run the server with the config file with `uwsgi project.ini`. Finally, making the system service file `/etc/systemd/system/uwsgi.service` as [here](http://uwsgi-docs.readthedocs.io/en/latest/Systemd.html). Finishing all of steps, run service `sudo systemctl start uwsgi`. However, we cannot check the result after this step if we locate the server to a socket file.

6, Installing [nginx](https://www.nginx.com/), change the config file `/etc/nginx/nginx.conf` or add a sub config file in `/etc/nginx/conf.d/`, adding a server node which locate to the port or socket file created by uwsgi server in last step. [Here](http://uwsgi-docs.readthedocs.io/en/latest/Nginx.html) are examples. Then run nginx service and check the server from brower. If your app were shown perfectlly, luckly the mission is finished.

### Problems

If you did not meet any problems in last 2 steps, that means you are so lucky or you unstand the configuration structure very well. Mostly, rookies like me would meet lots of problems during these steps. I will introduce some of cases I met.

Case 1,<br /> [Problem](https://stackoverflow.com/questions/16272542/uwsgi-fails-with-no-module-named-encoding-error) about python module not found when running `uwsgi project.ini`.

It is mainly because that python path setting is not right, the uwsgi tools is from one version of python and the others packages are from another version. Check the enviroment settings of python and virtualenv settings calefully and you could find what is missing. Or reboot the machine, for me, it solved my problem, I think maybe some cache data is not refreshed.

Case 2,<br />
[Problem](https://stackoverflow.com/questions/23863852/no-python-application-found-uwsgi-nginx-ubuntu-13) about no python app found.

It is a project path setting problem, try to put your ini file to the project folder and run again, it should be solved.

Case 3,<br />
Everything crash when start uwsgi service.

The uwsgi service is using another user session to run, so every enviroment setting of your current user will be losted in the uwsgi service process session. Write some commands in your 'uwsgi.service' file such as `export DATABASE_URL=**` or `source /virtualenv/activate`. There is a similar problem to config other service such as crontab.

Case 4,<br />
File premission for socket file after running nginx.

Add commands to ini file to give high file premission to nginx. like,
```
chown-socket = nginx
chmod-socket = 666
```
### Conclusion
These are the problems I met, we need to verify each small step during the configuration, because one tiny missing could casue you a lot of time to search it. And the situations between servers are not same, so it is also hard to find the solution directly from the internet. If you do not want to spend time on these troubles, you could use PaaS platform such as [AWS](https://aws.amazon.com/), [google app engine](https://cloud.google.com/appengine/), [heroku](heroku.com) or [pythonanywhere](https://www.pythonanywhere.com).
