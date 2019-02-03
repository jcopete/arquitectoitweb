---
layout: post
title: Enlace a un post en Jekyll
excerpt: "Cómo podemos crear un enlace a un post que exista dentro de Jekyll."
categories: jekyll
tags: [post,blog,jekyll]
image:
  feature: covers/write.jpg
  credit: Wim Mulder
  creditlink: https://www.flickr.com/photos/wimmulder/
comments: true
share: true
author: victor_cuervo
---

El código fuente sería:

<pre>
{{ site.baseurl }}llave-tantoporciento post_url nombre-de-post %}
</pre>

https://jekyllrb.com/docs/liquid/tags/#linking-to-posts

[Jekyll]: {{site.url}}/jekyll/
