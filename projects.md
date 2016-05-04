---
layout: page
title: Projects
---

{% for category in site.categories %}
	{% capture cat %}{{ category | first }}{% endcapture %}

### {{ cat }}
	{% for post in site.categories[cat] %}
		* {{ post.date | date: "%B %d, %Y" }} &raquo; [ {{ post.title }} ]({{ post.url }})
	{% endfor %}
{% endfor %}