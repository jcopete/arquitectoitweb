---
layout: page
title: NoSQL
excerpt: "Artículos sobre las posibilidades que nos ofrecen las bases de dato no estructuradas o bases de datos NoSQL"
image:
    feature: covers/nosql.jpg
    credit: netzanette
    creditlink: https://www.flickr.com/photos/netzanette/
search_omit: true
---

{% assign categoria = site.data.categories | where:"title","nosql" %}
{{ categoria[0].description }}

<ul class="post-list">
{% for post in site.categories.nosql %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% include date-es.html date=post.date %}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
