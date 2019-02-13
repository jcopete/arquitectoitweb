---
layout: page
title: DocumentDB
excerpt: "DocumentDB nos ofrece una alternativa a MongoDB para disponer de un cluster totalmente gestionado por AWS."
image:
  feature: covers/documentdb.jpg
  credit: Samuel Zeller
  creditlink: https://unsplash.com/photos/vpR0oc4X8Mk
search_omit: true
---

{% assign categoria = site.data.categories | where:"title","documentdb" %}
{{ categoria[0].description }}

<ul class="post-list">
{% for post in site.categories.documentdb %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% include date-es.html date=post.date %}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
