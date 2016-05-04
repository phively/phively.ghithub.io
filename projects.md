---
layout: page
title: Projects
permalink: /category/
---

{% for category in site.categories %}
{% capture cat %}{{ category | first }}{% endcapture %}

<h2>{{ cat | capitalize }}</h2>
	<ul>
	{% for post in site.categories[cat] %}
	  <li>
	  <p><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
	     <span class="date"> - {{ post.date | date_to_long_string }}</span></p>
	  </li>
	{% endfor %}
	</ul>

{% endfor %}