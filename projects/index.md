---
layout: page
title: Projects
---

{% for category in site.categories %}
  * {{ category | first }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}