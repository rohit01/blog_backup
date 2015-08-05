---
layout: page
title: Uttarakhand
categories:
  - social
tags:
  - photography
  - uttarakhand
  - rohit01
  - rohit.io
  - Rohit Gupta
disqus_comments: true
description: Uttarakhand Photos
thumbnail: /photos/album/uttarakhand/preview.jpg
no_of_pics: 5
---

<h1 align="center">{{page.title}}</h1>

{% for i in (1..page.no_of_pics) %}
<p>
  <a href="./hd/{{i}}.jpg">
    <img src="./regular/{{i}}.jpg" alt="{{page.title}}" style="border: 1px outset gray;">
  </a>
</p>
{% endfor %}
