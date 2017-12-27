---
layout: page
title: Front Development
excerpt: "Análisis de los frameworks y tecnologías para el desarrollo de las capas front de las aplicaciones. Revisión de los dispositivos, navegadores,..."
image:
  feature: covers/front.jpg
---

{% assign categoria = site.data.categories | where:"title","front" %}
{{ categoria[0].description }}

<ul class="post-list">
{% for post in site.categories.front %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% include date-es.html date=post.date %}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
