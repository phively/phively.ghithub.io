---
layout: page
title: Projects
---

{% for category in site.categories %}
  * {{ category | first }}"{% unless forloop.last %},{% endunless %}
{% endfor %}