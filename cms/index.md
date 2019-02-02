---
layout: page
title: CMS
excerpt: "Artículos sobre los CMS o Gestores de Contenidos."
image:
  feature: covers/cms.jpg
  credit: mightymightymatze
  creditlink: https://www.flickr.com/photos/mightymightymatze/
---

{% assign categoria = site.data.categories | where:"title","cms" %}
{{ categoria[0].description }}

<ul class="post-list">
{% for post in site.categories.cms %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% include date-es.html date=post.date %}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
