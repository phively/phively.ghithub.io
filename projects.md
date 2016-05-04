---
layout: page
title: Projects
permalink: /category/
---

{% for category in site.categories %}
{% capture cat %}{{ category | first }}{% endcapture %}

{{ cat | capitalize }}
	{% for post in site.categories[cat] %}
	  * {{ post.date | date: "%B %d, %Y" }} &raquo; [{{ post.title }}]({{ post.url | prepend: site.baseurl }})
	{% endfor %}
{% endfor %}