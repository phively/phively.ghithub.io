---
layout: page
title: Tags
---

{% capture taglist %}

{% assign tags_list = site.tags | sort %}

{% if tags_list.first[0] == null %}

{% for tag in tags_list %}
[{{ tag }} ({{ tag | size }})](#{{ tag | slugify }}) 
{% endfor %}
{% else %}
{% for tag in tags_list %}
[{{ tag[0] }}](#{{ tag[0] | slugify }}) 
{% endfor %}

{% endif %}

{% endcapture %}

{{ taglist | strip_newlines }}

------

{% for tag in tags_list %}
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

{% assign tags_list = nil %}