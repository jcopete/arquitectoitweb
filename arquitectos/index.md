---
title: Arquitectos
excerpt: "Arquitectos que escriben en Arquitecto IT."
layout: page
permalink: /arquitectos/
image:
  feature: portada.png
---

<div class="cards">
{% for item in site.data.authors %}

  <a href="/arquitecto/{{ item[0] | slugify }}">
  <div class="card">
      {% if item[1].avatar contains 'http' %}
        <img src="{{ item[1].avatar }}" class="bio-photo img-responsive" alt="{{ item[1].name }} bio photo"/>
      {% elsif item[1].avatar %}
        <img src="{{ site.url }}/images/{{ item[1].avatar }}" class="bio-photo img-responsive" alt="{{ item[1].name }} bio photo"/>
      {% endif %}
      <div class="container">
        <h4><b>{{item[1].name}}</b></h4>               
      </div>

      {% assign usuario = item[0] %}
      {% assign post_usuario = site.posts|where_exp:"item","item.author == usuario" %}

      <div class="card-footer"><a href="/arquitecto/{{ item[0] | slugify }}"><i class="fa fa-pencil-square-o" aria-hidden="true"></i> {{post_usuario.size}} {% if post_usuario.size==1 %}artículo{% else %}artículos{% endif %}</a></div>    
  </div>
  </a>
{% endfor %}
</div>
