---
layout: page
title: Postman
excerpt: "Postman es un entorno de desarrollo API First que nos permite gestionar parte del ciclo de vida del API Management."
image:
  feature: covers/postman.jpg
  credit: Marius Christensen
  creditlink: https://unsplash.com/photos/UXfi8LyqGDk
search_omit: true
---

{% assign categoria = site.data.categories | where:"title","postman" %}
{{ categoria[0].description }}

<ul class="post-list">
{% for post in site.categories.postman %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% include date-es.html date=post.date %}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
