---
layout: navpage-top
title: Categories
---

<!-- Adapted from https://github.com/LanyonM/lanyonm.github.io/blob/master/tags.html -->

{% capture site_cats %}{% for cat in site.categories %}{{ cat | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
<!-- site_cats: {{ site_cats }} -->
{% assign cat_words = site_cats | split:',' | sort %}
<!-- cat_words: {{ cat_words }} -->

<div id="categories">
  {% for cat in cat_words) %}
    <!-- Do not include a category for "projects" only its subfolders -->
    {% if cat == "projects" %} {% continue %} {% endif %}
    <a href="#{{ cat | cgi_escape }}">{{ cat }}<sup>{{ site.categories[cat] | size }}</sup></a>
  {% endfor %}


  {% for item in (0..site.categories.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ cat_words[item] | strip_newlines }}{% endcapture %}
    <!-- Do not include a category for "projects" only its subfolders -->
    {% if this_word == "projects" %} {% continue %} {% endif %}
  <h2 id="{{ this_word | cgi_escape }}">{{ this_word }}</h2>
  <ul class="posts">
    {% for post in site.categories[this_word] %}
    {% if post.title != null %}
    <li itemscope><a href="{{ post.url }}##">{{ post.title }}</a> &ndash; <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%F" }}</time></span></li>
    {% endif %}{% endfor %}
  </ul>
  {% endunless %}{% endfor %}
</div>