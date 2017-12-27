---
layout: post
title: Diseños Web Multimedia con Popcorn
excerpt: "Uso del framework Popcorno para poder crear diseños multimedia basados en vídeo para tu web."
categories: front
tags: [multimedia]
image:
  feature: covers/multimedia.jpg
comments: true
share: true
author: victor_cuervo
---

La aparición de los elementos [VIDEO][video] y [AUDIO][audio] en **HTML5 ha simplificado la capacidad de insertar elementos multimedia en nuestros diseños webs**. Si bien, el estado primigenio de la especificación HTML5 hace que sea complicado mantener la compatibilidad de código para diferentes navegadores.

# Popcorn: Unificando el elemento VIDEO
**Popcorn es un proyecto de Mozilla que pretende dar un interface unificado y sencillo para el tratamiento de los elementos multimedia en las páginas web**.

De esta manera, lo primero que nos ofrece Popcorn es el **framework Popcorn.js**, el cual, mediante un sistema de eventos facilita la interacción con los elementos multimedia. Así Popcorn.js nos permite centrarnos en lo que realmente queremos hacer simplificandonos el control y gestión del vídeo.

**Popcorn.js estandariza las propiedades del elemento [HTMLMediaElement][mediaelement]**. Ya que a día de hoy no tiene una implementación unificada en todos los navegadores. Cada versión del framework tiene unos 1400 test de regresión para asegurar la compatibilidad con los navegadores web.

# Popcorn: Realizando mashups multimedia
Pero Popcorn no se queda en una simplificación de la gestión de vídeos, si no que su idea es el **poder proporcionar una experiencia multimedia completa al usuario**. De esta forma, el framework Popcorn.js cuenta con multiples funcionalidades para acceder a recursos multimedia: fotos, tweets, wikipedia,... los cuales iremos cargando, mostrando y ocultando en el avance del vídeo.

Alrededor del proyecto Popcorn han nacido un ecosistema de proyectos y librerías que complementan a este framework, dando la posibilidad de extender su uso.

Entre los plugins podemos encontrar: Twitter, Flickr, Lastfm, Linkedin, OpenMap, Wikipedia, Google Maps,...

# A descargarse Popcorn
Si quieres trabajar con el framework Popcorn.js tienes que saber que la versión actual de Popcorn es **Popcorn 1.2**. Las librerías que necesitarás son:

* <a title="Popcorn para desarrollo" href="http://popcornjs.org/code/dist/popcorn-complete.js">Librería Popcorn para desarrollo</a>
* <a title="Librería Popcorn para producción" href="http://popcornjs.org/code/dist/popcorn-complete.js">Librería Popcorn para producción</a>

Otra opción es [personalizarse la librería de producción mediante un builder][personalizarpopcorn].

Si te has descargado Popcorn es bueno que ahora le eches un vistazo a la [documentación de popcorn, sus apis y demos][popcorn].

# Algo de código con Popcorn
El uso del framework Popcorn.js es muy sencillo. Veamos algunas pequeñas líneas de código sobre lo que podemos hacer:

Cargando Popcorn:

~~~html
<script src="http://popcornjs.org/code/dist/popcorn-complete.min.js" type="text/javascript"></script>

<video id="ourvideo" src="http://videos.mozilla.org/serv/webmademovies/popcornplug.mp4" width="300" height="180">
  <source src="http://videos.mozilla.org/serv/webmademovies/popcornplug.ogv" />
  <source src="http://videos.mozilla.org/serv/webmademovies/popcornplug.webm" />
</video

<div id="footnote"></div>
~~~

Creando texto en un momento determinado del vídeo:

~~~javascript
var popcorn = Popcorn( "#ourvideo" );

popcorn.footnote({
  start: 2,
  end: 5,
  target: "footnote",
  text: "Pop!"
});
~~~

Integrando Popcorn con las fotos de Flickr:

~~~javascript
var pop = Popcorn( "#video" );

pop.flickr({
  start: 5,
  end: 15,
  userid: "35034346917@N01",
  target: "flickrdiv"
});
~~~

Integrando Popcorn con el timeline de Twitter:

~~~javascript
pop.twitter({
  start: 5,
  end: 15,
  title: "Steve Song",
  src: "@stevesong",
  target: "twitterdiv",
});
~~~

# Ejemplos de Webs hechas con Popcorn
Algunas de las demos que puedes visualizar con Popcorn son:


* [Know you exit][knowyourexit], un experimento musical con gente componiendo alrededor del mundo. La composición de música y vídeo queda integrada con tweets de Twitter y geolocalizaciones.
* [Zaragoza Public Spaces][zaragoza], vídeo que nos muestra sitios de interés de Zaragoza integrando localizaciones con Google Maps y texto anexo al vídeo.
* [Open Images, Open Data][openimages], una iniciativa holandesa que nos muestra como se puede enriquecer un vídeo con contenido multimedia diverso obtenido de Wikipedia, Google Maps, repositorios de los museos de Holanda,...
* [Color Tracker][colortracker], como poder seguir un color dentro del vídeo y añadirle información.
* ... [otras demos][otrasdemos].

>Aunque hemos comentado que Mozilla Popcorn es un proyecto que soporta diferentes navegadores, es muy recomendable visualizarlo con Firefox. :-D

# Popcorn Maker (proyecto Butter): editando nuestros vídeos
Adicionalmente al framework Popcorn.js el proyecto **Popcorn está construyendo Popcorn Maker**. Que es conocido como el proyetco Butter.

**Popcorn Maker es un editor de vídeos en formato web**. De esta forma el editor Popcorn Maker creará de forma dinámica el código del framework Popcorn.js en base a las acciones que definamos: insertar elementos en el vídeo, realizar overlaping,...

Todo **el trabajo con Popcorn Maker se realiza de forma visual**, sin tener que tirar ni una sola línea de código.

![PopCorn Maker]({{ site.url }}/images/front/multimedia/popcorn-maker.png)

A día de hoy podemos probar la [Preview de Popcorn Maker][popcornpreview] y habrá que esperar hasta noviembre 2012 para poder disponer de la primera versión de Popcorn Maker.

Adicionalmente podemos [bajarnos el código de Popcorn Maker][popcorncodigo], realizar pruebas, reportar bugs, extenderlo,...

> Puedes encontrar más información sobre el proyecto en **[Mozilla Popcorn][popcornmozilla]** y **[@popcornjs][popcorntwitter]**

[video]: http://w3api.com/wiki/HTML5:VIDEO
[audio]: http://w3api.com/wiki/HTML5:AUDIO
[mediaelement]: http://w3api.com/wiki/DOM:HTMLMediaElement
[personalizarpopcorn]: http://mozillapopcorn.org/build-tool/
[popcorn]: http://popcornjs.org/
[knowyourexit]: http://www.robmorrismusic.com/knowyourexit/
[zaragoza]: http://www.samuelnegredo.com/zaragoza-public-spaces/gran-via.htm
[openimages]: http://rdbg.tuxic.nl:4444/apps/openbeelden
[colortracker]: http://anavallasuiza.com/popcorn/
[otrasdemos]: http://popcornjs.org/demos
[popcornpreview]: http://mozillapopcorn.org/popcorn-maker/
[popcorncodigo]: https://github.com/mozilla/butter
[popcorntwitter]:https://twitter.com/popcornjs
[popcornmozilla]: http://mozillapopcorn.org
