---
layout: page
title: Arquitecto IT
excerpt: "Análisis de tecnologías por Arquitectos IT"
search_omit: true
image:
  feature: portada.png
---
# ¿Qué es Arquitecto IT?
En Arquitecto IT nos hemos juntado un grupo de Arquitectos IT que tienen ganas de hablar sobre nuevas tecnologías, de cómo estas nos pueden ayudar en el desarrollo de proyectos. Arquitectos IT que quieren compartir sus experiencias y conocimientos.

Buscamos la conversación, la crítica, el aprendizaje, el debate,… pero siempre desde el lado positivo, desde el lado de la colaboración, del compañerismo, del aporte de soluciones por parte de la gente. Buscamos que, de forma ordenada, la gente exprese sus visiones, de a conocer sus puntos de vista sobre las cosas que aquí se escriben.

# Editorial
{% assign editorial = site.categories['editorial'][0] %}
<div class="contenedor">  
  <img src="{{ site.url }}/images/{{ editorial.image.feature }}" class="img-responsive"/>
  <div class="bottom-right">
    <h4><a href="{{ site.url }}{{ editorial.url }}">{{ editorial.title }}</a></h4>
  </div>
</div>

# Últimos Artículos
<ul class="post-list">
{% for post in site.posts limit:10 %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{% include date-es.html date=post.date %}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>
