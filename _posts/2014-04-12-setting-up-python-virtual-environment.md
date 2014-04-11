---
layout: post
categories: [python, virtial environment, venv]
disqus_comments: true
date: 2014-04-12 00:25:00 IST
title: Setting up python vitual environment
---

Using python virtual environment for development is highly recommended and is widely used by python programmers. Debian/Ubuntu commands to install python virtualenv are as follows:

* Install required packages:

```bash
    $ sudo apt-get install python-pip
    $ sudo pip install virtualenv
````

Create a virtualenv:

```bash
    $ virtualenv [--no-site-packages] venv
````

Activate virtualenv:

```bash
    $ source venv/bin/activate
````

Once the virtualenv is activated, use pip to install libraries. For example:
```bash
    (venv)$ pip install gevent redis ipython
````

The above example installs python packages: gevent, redis and ipython. To deactivate virtualenv:

```bash
    (venv)$ deactivate
````

Virtualenv can efectively help you maintain library dependencies for different projects. You can even maintain different version of python using virtualenv. It is even used for single installation of Python in a System.

**And as always, Thanks for reading :)**
