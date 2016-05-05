---
layout: page
title: Categories
---

{% for category in site.categories %}
{% capture cat %}{{ category | first }}{% endcapture %}

{% if cat == "projects" %}
  {% continue %}
{% endif %}

### {{ cat | camelcase }}
{% for post in site.categories[cat] %}
  * {{ post.date | date: "%B %d, %Y" }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}

{% endfor %}