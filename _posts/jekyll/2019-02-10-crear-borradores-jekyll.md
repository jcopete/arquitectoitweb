---
layout: post
title: Crear borradores en Jekyll
excerpt: "Cómo crear entradas en formato borrador cuando estemos publicando con Jekyll."
categories: jekyll
tags: [blog,borradores]
image:
  feature: covers/write.jpg
  credit: Wim Mulder
  creditlink: https://www.flickr.com/photos/wimmulder/
comments: true
share: true
author: victor_cuervo
---

Cuando estamos trabajando con el [sistema de blog Jekyll][Jekyll] estaremos trabajando con documentos o artículos que sean públicos, pero también estaremos trabajando con documentos o artículos que sean borradores.

Si queremos crear borradores en Jekyll será "tan sencillo" cómo que publiquemos dichos borradores dentro de la carpeta **_drafts**.

La estructura que nos encontraremos dentro de nuestro blog [Jekyll][Jekyll] será algo parecido a lo siguiente:

~~~sh
+ blog
 + \_data
 + \_drafts
 + \_includes
 + \_posts
~~~

Así que nuestro borrador simplemente tendrá que estar dentro del directorio **_drafts**.

**¿Qué sucederá cuando arranque el servidor [Jekyll][Jekyll]?** Pues que el artículo que está en borradores dentro de la carpeta **_drafts** no será visualizado.

~~~sh
$ jekyll server --watch
~~~

Para que podamos visualizar los borradores dentro del renderizado de [Jekyll][Jekyll] deberemos de arrancar el servidor con la opción `--drafs`.

Así ejecutaremos lo siguiente:

~~~sh
$ jekyll server --watch --drafts
~~~

Cuando carguemos el servidor podremos comprobar que los borradores se pueden visualizar.

Cuando queramos publicar uno de los artículos que tengamos en borradores será tan sencillo como moverlo de la carpeta **_drafts** a la carpeta **_posts**.

Así de sencillo es crear borradores en [Jekyll][Jekyll].

[Jekyll]: {{site.url}}/jekyll/
