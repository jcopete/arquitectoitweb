---
layout: page
title: MongoDB
excerpt: "Análisis de las funcionalidades y capacidades que nos ofrece la base de datos orientada a documentos JSON MongoDB."
image:
  feature: covers/hoja.jpg
  credit: Martin Castro
  creditlink: https://unsplash.com/photos/dlMui5b3yR4
search_omit: true
---

{% assign categoria = site.data.categories | where:"title","mongodb" %}
{{ categoria[0].description }}

<ul class="post-list">
{% for post in site.categories.mongodb %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% include date-es.html date=post.date %}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
