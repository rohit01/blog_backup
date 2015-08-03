---
layout: page
title: Gurgaon
categories:
  - social
tags:
  - photography
  - gurgaon
  - rohit01
  - rohit.io
  - Rohit Gupta
description: Gurgaon Photos
thumbnail: /photos/album/nandi-hills/preview.jpg
no_of_pics: 9
---

<h1 align="center">{{page.title}}</h1>

{% for i in (1..page.no_of_pics) %}
<p>
  <a href="./hd/{{i}}.jpg">
    <img src="./regular/{{i}}.jpg" alt="{{page.title}}" style="border: 1px outset gray;">
  </a>
</p>
{% endfor %}
