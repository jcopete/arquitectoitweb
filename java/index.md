---
layout: page
title: Java
excerpt: "Análisis de las tecnologías alrededor del mundo Java"
image:
  feature: covers/java.png
---

{% assign categoria = site.data.categories | where:"title","java" %}
{{ categoria[0].description }}

<ul class="post-list">
{% for post in site.categories.java %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% include date-es.html date=post.date %}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
