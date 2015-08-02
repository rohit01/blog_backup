---
layout: page
title: Nandi Hills
categories:
  - social
tags:
  - photography
  - nandi hills
  - rohit01
  - rohit.io
  - Rohit Gupta
description: Nandi Hills
thumbnail: ./preview.jpg
no_of_pics: 28
---

<h1 align="center">{{page.title}}</h1>

{% for i in (1..page.no_of_pics) %}
<p>
  <a href="./hd/{{i}}.jpg">
    <img src="./regular/{{i}}.jpg" alt="{{page.title}}" style="border: 1px outset gray;">
  </a>
</p>
{% endfor %}
