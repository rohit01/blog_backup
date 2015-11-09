---
layout: page
title: Gokarna
categories:
  - social
tags:
  - photography
  - gokarna
  - rohit01
  - rohit.io
  - Rohit Gupta
disqus_comments: true
description: Gokarna Photos
thumbnail: /photos/album/gokarna/preview.jpg
no_of_pics: 42
---

<h1 align="center">{{page.title}}</h1>

{% for i in (1..page.no_of_pics) %}
<p>
  <a href="./hd/{{i}}.jpg">
    <img src="./regular/{{i}}.jpg" alt="{{page.title}}" style="border: 1px outset gray;">
  </a>
</p>
{% endfor %}
