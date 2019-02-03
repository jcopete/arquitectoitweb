---
layout: post
title: ¿Qué es Jekyll?
excerpt: "Artículo que nos hace una pequeña introducción sobre qué es Jekyll y qué beneficios tenemos de utilizarlo."
categories: jekyll
tags: [blog,markdown,liquid,github]
image:
  feature: covers/write.jpg
  credit: Wim Mulder
  creditlink: https://www.flickr.com/photos/wimmulder/
comments: true
share: true
author: victor_cuervo
---

Seguro que si alguna vez has creado un blog te habrás encontrado con diferentes soluciones de software para poder montarlo. Raro sería si no has acabado utilizando *WordPress*, *Joomla* o *Drupal*. Llegado ese punto te habrás encontrado en más de una ocasión afinando los tiempos de respuesta asociados al acceso al contenido en las bases de datos.

Y es que más rápido que servir una página estática no vamos a encontrar nada. Así que alternativas como asociar un **CDN (Content Delivery Network)** o **la conversión a ficheros estáticos** de nuestras webs son una gran alternativa o complemento.

Dentro de la **gestión de contenidos mediante plantillas y ficheros estáticos** tenemos algunos generadores de contenido como [Jekyll][Jekyll].

## Entonces, ¿Qué es Jekyll?
[Jekyll][Jekyll] **es un generador de páginas estáticas para la construcción de webs**, principalmente enfocado a blogs, aunque nos sirve para contruir cualquier tipo de página web. Está escrito en **Ruby** y fue desarrollado por *Tom Preston-Werner*, uno de los cofundadores de **GitHub**.

[Jekyll][Jekyll] es utilizado como el motor de creación de todas las páginas que se sirven en **GitHub Pages**.

La idea de [Jekyll][Jekyll] no es la de utilizar una base de datos para almacenar el contenido como hacen los [CMS o Gestores de Contenidos][CMS] tradicionales, si no que el contenido de nuestra web se define mediante ficheros de texto en formatos *markdown*.

Si que comparte con los [CMS o Gestores de Contenidos][CMS] la capacidad de disponer de plantillas para el diseño de la web. En este caso las plantillas de [Jekyll][Jekyll] están basadas en [Liquid][Liquid].

El *proceso de [Jekyll][Jekyll]* combina el contenido de los ficheros en *markdown* con las plantillas de [Liquid][Liquid] para **generar un sitio web totalmente creado por ficheros estáticos**.

Al tener un **sitio web totalmente creado por ficheros estáticos** cualquier servidor web, ya sea [NGinx][nginx], *Apache*,... nos permitirá montar de una forma muy sencilla nuestra página web.

## ¿Qué podemos hacer con Jekyll?

Entre muchas otras cosas, con [Jekyll][Jekyll] podemos:

* Crear **páginas web** o **entradas post**.
* Agrupar las entradas o post en **categorias**.
* Definir **etiquetas** para las páginas o las entradas.
* **Asociar un usuario** a cada uno de los contenidos.
* Asignar una **fecha de creación** a cada uno de los contenidos.
* Podemos **personalizar los enlaces permanentes** para cada uno de los contenidos.
* Podemos crear un **buscador de contenidos**.

## ¿Es Jekyll un CMS?

Podríamos tratar a [Jekyll][Jekyll] como un [CMS o Gestor de Contenidos][CMS] ya que cumple con [algunas de sus características][CMSCaracteristicas], si bien carece de un interface que haga que un usuario de un perfil no técnico pueda contribuir con contenidos de una forma sencilla.

Para resolver este pequeño handicap hay algunas soluciones que han nacido alrededor de [Jekyll][Jekyll] para proporcionar un interface orientado a usuarios que contribuyen con contenidos.

Así tenemos herramientas como [CloudCannon][CloudCannon], [Forestry][Forestry], [Netlify][Netlify] o [SiteLeaf][SiteLeaf] que nos ayudan ofreciendo un interface para gestionar el contenido de una forma sencilla.

## Cómo empezar a utilizar Jekyll
Para poder empezar a trabajar con [Jekyll][Jekyll] simplemente necesitas tener instalado *Ruby* en tu ordenador. Si ya cuentas con *Ruby* puedes instalarte [Jekyll][Jekyll] como una *gema*. Es tan sencillo como ejecutar lo siguiente:

~~~sh
$ gem install bundler jekyll
$ jekyll new mi-web
$ cd mi-web
$ bundle exec jekyll serve
# => Abre en un navegador http://localhost:4000
~~~

Tienes mucha más información en [la web de Jekyll][JekyllWeb].

[Jekyll]: {{site.url}}/jekyll/
[CMS]: {{site.baseurl}}{% post_url /cms/2019-02-01-que-es-un-cms %}
[Liquid]: https://shopify.github.io/liquid/
[nginx]: {{site.url}}/nginx/
[CMSCaracteristicas]: {{site.baseurl}}{% post_url /cms/2019-02-01-10-caracteristicas-cms %}
[CloudCannon]: https://cloudcannon.com/
[Forestry]: https://forestry.io/
[Netlify]: https://www.netlify.com/
[SiteLeaf]: https://www.siteleaf.com/
[JekyllWeb]: https://jekyllrb.com/
