---
layout: category
title: Projects
category: Projects
---

{% for category in site.categories %}
  * {{ category | first }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}