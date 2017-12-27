---
layout: page
title: Categorías
excerpt: "Categorías en Arquitecto IT"
search_omit: true
image:
  feature: portada.png
---

<div class="cards">
{% assign categories_list = site.categories %}
{% for category in categories_list %}
  {% assign metacategory = site.data.categories | where:"title",category[0] %}
      <a href="/{{category[0]}}">
      <div class="card">
        {% if metacategory[0] %}
          <img src="{{ site.url }}/images/{{metacategory[0].image}}" alt="category[0]" style="width:100%">
          <div class="container">
            <h4><b>{{metacategory[0].name}}</b></h4>
            <p>{{metacategory[0].description}}</p>          
          </div>
          <div class="card-footer"><i class="fa fa-pencil-square-o" aria-hidden="true"></i> {{category[1].size}} {% if category[1].size==1 %}artículo{% else %}artículos{% endif %}</div>
        {% else %}
          <img src="{{ site.url }}/images/covers/default.jpg" alt="category[0]" style="width:100%">
          <div class="container">
            <h4><b>{{category[0]}}</b></h4>          
          </div>
          <div class="card-footer"><i class="fa fa-pencil-square-o" aria-hidden="true"></i> {{category[1].size}} {% if category[1].size==1 %}artículo{% else %}artículos{% endif %}</div>
        {% endif %}      
      </div>
      </a>
  {% endfor %}  
{% assign categories_list = nil %}
</div>
