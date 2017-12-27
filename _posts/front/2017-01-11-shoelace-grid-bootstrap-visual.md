---
layout: post
title: Shoelace&#58; Grid Bootstrap Visual
excerpt: "El planteamiento del Diseño Responsable se basa en tener en cuenta el dispositivo y el contexto que el usuario emplea para acceder al contenido."
categories: front
tags: [responsive design, bootstrap]
image:
  feature: covers/responsive.png
comments: true
share: true
author: victor_cuervo
---

Una de las cosas más potentes del framework de [Bootstrap][Bootstrap] es la capacidad que tiene para el desarrollo de webs responsive. Para ello [Bootstrap][Bootstrap] nos proporciona el concepto de Grid. [Shoelace][Shoelace] es una herramienta que nos permite desarrollar un grid [Bootstrap][Bootstrap] de manera visual. Es decir, de una manera sencilla nos permite establecer cómo será el diseño del Grid para cada uno de los dispositivos.

Pero lo primero que vamos a hacer es explicar un poco de la teoría de cómo funciona el grid responsive de [Bootstrap][Bootstrap]. [Bootstrap][Bootstrap] lo que hace es dividir un contenedor en doce elementos. El contenedor es representado con la clase ```container```:

~~~html
<div class="container"> ... </div>
~~~

Dentro del contenedor podemos incluir filas de elementos. En este caso es el elemento ```row``` el que utiliza para representar la fila.

~~~html
<div class="container">
  <div class="row">...</div>
</div>
~~~

Ahora para los elementos define 4 clases ```col-xs``` para los dispositivos móviles, ```col-sm```, para las tablets, ```col-md``` para los ordenadores y ```col-lg``` para las pantallas panorámicas.

A cada una de las clases le añadiremos un número con el cual indicaremos el número de espacios (de 1 a 12) que ocupa. Así por ejemplo podemos definir que para una tablet hay dos elementos por fila.

~~~html
<div class="container">
  <div class="row">
    <div class="col-sm-6"></div>
    <div class="col-sm-6"></div>
    <div class="col-sm-6"></div>
    <div class="col-sm-6"></div>
  </div>
</div>
~~~

Vemos que entre los dos elementos siempre suman 12. Podemos combinar los estilos, de esta forma podemos decir que en el caso de ordenadores hay 4 elementos por fila. Así el código será el siguiente:

~~~html
<div class="container">
  <div class="row">
    <div class="col-sm-6 col-md-3"></div>
    <div class="col-sm-6 col-md-3"></div>
    <div class="col-sm-6 col-md-3"></div>
    <div class="col-sm-6 col-md-3"></div>
  </div>
</div>
~~~

Vemos que los elementos col-md también suman 12.

Como esto se nos puede complicar es cuando podemos acudir a [Shoelace][Shoelace] que nos ofrece un interface visual muy sencillo para definir como queremos que se vean nuestros elementos en cada una de las visualizaciones: *móvil, table, pc y pantallas panorámicas*.

![Pantalla de Shoelace]({{ site.url }}/images/front/responsive/shoelace.jpg)

Simplemente tendremos que elegir el tipo de dispositivo y situar los elementos dentro de él. De esta manera Shoelace nos va generando el código [HTML][HTML] el cual podremos copiar.

Shoelace es una herramienta muy útil para diseñar los Grid de [Bootstrap][Bootstrap] de una manera visual y sencilla.

[HTML]: http://www.manualweb.net/html/
[Bootstrap]: http://www.manualweb.net/bootstrap/
[Shoelace]: http://shoelace.io/
