---
layout: page
title: Tags
---

{% assign tags_list = site.tags %}

<span class="nowrap">

{% if tags_list.first[0] == null %}

{% for tag in tags_list %}
[ {{ tag }} ](#{{ tag | slugify }})
{% endfor %}
{% else %}
{% for tag in tags_list %}
[ {{ tag[0] }} ](#{{ tag[0] | slugify }})
{% endfor %}

{% endif %}

</span>

{% assign tags_list = nil %}

------

{% for tag in site.tags  %}
#### <a name="{{ tag[0] | slugify }}">{{ tag[0] }}</a>

{% assign pages_list = tag[1] %}
{% for post in pages_list reversed %}
{% if post.title != null %}
{% if group == null or group == post.group %}
  * {{ post.date | date: "%B %d, %Y" }} &raquo; [{{ post.title }}]({{ site.url }}{{ post.url | prepend: site.baseurl }})
{% endif %}
{% endif %}
{% endfor %}
{% assign pages_list = nil %}
{% assign group = nil %}

{% endfor %}