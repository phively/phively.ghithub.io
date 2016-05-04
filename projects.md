---
layout: page
title: Projects
permalink: /category/
---

{% for category in site.categories %}
{% capture cat %}{{ category | first }}{% endcapture %}

<h2>{{ cat | capitalize }}</h2>
	{% for post in site.categories[cat] %}
	  * {{ post.date | date: "%B %d, %Y" }} &raquo; [{{ post.title }}]({{ post.url | prepend: site.baseurl }})
	{% endfor %}
{% endfor %}