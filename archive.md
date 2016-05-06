---
layout: navpage
title: Archive
---

<!-- Adapted from http://benjaminblog.ml/Nice_Blog/archive/ -->

{% assign is_first = true %}
{% for post in site.posts %}

  {% capture this_year %}
    {{ post.date | date: "%Y" }}
  {% endcapture %}
  {% if is_first %}
  ## {{ this_year }}
  {% endif %}

  {% capture next_year %}
    {{ post.previous.date | date: "%Y" }}
  {% endcapture %}
  {% if this_year == next_year %}
    {% assign is_first = false %}
  {% else %}
    {% assign is_first = true %}
  {% endif %}

  * <a href="{{ post.url }}">{{ post.title }}</a> &ndash; {{ post.date | date: "%F" }}
	  
{% endfor %}