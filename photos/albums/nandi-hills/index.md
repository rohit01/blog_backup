---
layout: page
title: Photo Albums
categories:
  - social
tags:
  - photography
  - albums
  - rohit01
  - rohit.io
  - Rohit Gupta
description: Photography as a hobby!
thumbnail: /res/photos/albums.jpg
no_of_pics: 28
---

{% for i in (1..page.no_of_pics) %}
[![Nandi Hills](/res/photos/nandi-hills/{{i}}.jpg)](/res/photos/nandi-hills/{{i}}.jpg)
{% endfor %}

