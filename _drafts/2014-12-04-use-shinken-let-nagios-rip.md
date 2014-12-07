---
layout: post
date: 2014-12-04 12:49:00 IST
title: Use Shinken, let Nagios RIP!
categories:
  - technology
tags:
  - nagios
  - shinken
  - docker
thumbnail: /res/posts/use-shinken-let-nagios-rip/NinjaGreen.png
subtitle: Quick comparison and how to migrate your current Nagios setup to Shinken in less than 10 minutes
---

Nagios is a great monitoring tool. Some people still consider it as an IT standard for monitoring. There are many alternatives of Nagios. I find, Shinken as the most compatible and modern alternative. In this article, I will do a quick comparision, show you why and how to migrate your current Nagios setup to Shinken in less than 10 minutes (I am serious).

**Quick Introduction to Shinken**: Shinken was written by [Jean Gabès](https://twitter.com/naparuba) as a proof of concept for a new Nagios architecture. He proposed it as the new development branch of Nagios 4. This proposal was turned down by the Nagios authors, so Shinken became an independent network monitoring software application compatible with Nagios. Shinken is a Nagios Core replacement written in python.

Shinken vs Nagios:
==================

I have used both Nagios and Shinken. At [Knowlarity](http://www.knowlarity.com/), we did the big switch from Nagios to Shinken for our complete Infrastructure in just about a week. It helped to solve some of the fundamental problems which was hard in Nagios. Here are some of the reasons:

* **Reliability**: I was working on a NRPE notification plugin and deployed it in Nagios. I turned down a service to test it but to my surprise, Nagios was still showing it as green. The last executed time got updated in the UI but nothing happened under the hood. This issue happened randomly. I think, it could be because of a old version of Nagios 3.x. I never faced this issue in Shinken. The UI always displayed the truth.

* **Active Development**: I updated Nagios to the latest 4.x. The first impression was that nothing changed except colors in the user interface. In contrast, Shinken full architecture was revamped. Shinken 2.0 has a very modular design, easy installation, configuration and more features. Kudos to Shinken community.

* **Multi DC deployment**: At Knowlarity, we have data-centers at multiple cities and countries. Multi-DC deployment using nagios is difficult and it looks like a hack. In Shinken, I just added a new shinken-poller in all datacenters and I am done. Shinken configuration is still managed in a single place. Its distributed architecture is awesome.

* **Performance**: Nagios is written in C and is a lot faster than Shinken. However, shinken has some exciting proformance improvement modules like [booster-nrpe](https://github.com/shinken-monitoring/mod-booster-nrpe).

* **Modern**: IT industry has evolved. Its more dynamic, bigger and complex at the same time. Nagios is already left behind with same old features. On the other hand, Shinken has support for dynamic configuration, AWS hosts, a module installer and many more. The community is very active and responsive.

* **User Interface**: Nagios has a feature rich but same old interface for years. Shinken has a sleek and modern interface - WebUI. WebUI is really easy and simple but lack features. However, there are many third party interfaces available. I like to use WebUI and [Thruk](http://www.thruk.org/) at the same time. Thruk interface is similar to Nagios. So hardcore nagios users still feel at home.

* **Easy Switch**: Probably the best thing about shinken is that, it is like a plug and play replacement of Nagios core. Almost 100% compatible. Just dump your Nagios configuration in Shinken and it works. Some more details at their documentation website: [Feature comparison between Shinken and Nagios](http://shinken.readthedocs.org/en/latest/01_about/whatsnew.html)

Switch to Shinken in 3 easy steps:
=================================

1. Install [docker](https://docs.docker.com/installation/#installation). Select and pull one of the following docker image:

    * **Shinken**: It has basic shinken installation along with few must have modules like WebUI (Web Interface), standard nrpe plugins + few extra ones, nrpe-booster support and a lightweight web server (nginx). Link: <https://registry.hub.docker.com/u/rohit01/shinken/>
    * **Shinken Thruk**: Shinken (as written above) + Thruk web interface. Internal web server nginx is replaced with apache2. Link: <https://registry.hub.docker.com/u/rohit01/shinken_thruk/>
    * **Shinken Thruk Graphite**: Shinken Thruk (as written above) + graph support in WebUI. Graphs are stored and served using graphite. Retention is configured for 1 month on a per 2 minute basis. Link: <https://registry.hub.docker.com/u/rohit01/shinken_thruk_graphite/>

2. Clone project *docker_shinken*: <https://github.com/rohit01/docker_shinken>. You will see three directories corresponding to the docker images mentioned above. Go inside the directory corresponding to your selected image. You will see a directory named: [custom_configs/](https://github.com/rohit01/docker_shinken/tree/master/shinken_basic/custom_configs). Dump your Nagios configuration here. A default configuration for monitoring docker host is already defined. User login details can be updated in file: [htpasswd.users](https://github.com/rohit01/docker_shinken/blob/master/shinken_basic/custom_configs/htpasswd.users). File contains the documentation as comments.

3. Run the docker image. Expose TCP port 80 to the base machine and mount custom_configs directory to /etc/shinken/custom_configs. Sample execution:

    ```
    $ git clone https://github.com/rohit01/docker_shinken.git
    $ cd docker_shinken/shinken_basic
    $ sudo docker run -d -v "$(pwd)/custom_configs:/etc/shinken/custom_configs" -p 80:80 rohit01/shinken
    ```

Open your browser and visit these urls (Default credential - admin/admin):

1. **WebUI**: <http://localhost/>. Available on all three images.
2. **Thruk UI**: <http://localhost/thruk/>. Available on shinken_thruk and shinken_thruk_graphite images.
3. **Graphs**: <http://localhost/service/docker_shinken/http_port_7770#graphs>. Available only on shinken_thruk_graphite image.

### Please Note:

* Configuration changes are required only in one place/directory: custom_configs
* The nrpe plugins installation directory is /usr/lib/nagios/plugins.
* If you are using custom NRPE plugins, please mount your plugins directory inside docker container at /usr/local/custom_plugins. You need to modify resource path accordingly.

If you have any question, I will be happy to answer them in comments. **And as always, Thanks for reading!**
