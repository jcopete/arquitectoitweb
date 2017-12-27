---
layout: post
title: Layout Adaptable en Diseños "Sensibles"
excerpt: "El planteamiento del Diseño Responsable se basa en tener en cuenta el dispositivo y el contexto que el usuario emplea para acceder al contenido."
categories: front
tags: [responsive design, media queries, accesibilidad]
image:
  feature: covers/responsive.png
comments: true
share: true
author: juan_manuel_garcia
---

# Que tu diseño sea "Sensible" al contexto del usuario
Dentro del ámbito de la Accesibilidad, encontramos un punto muy importante, que todo arquitecto y desarrollador Web debería de tener en cuenta a la hora de plantear la Arquitectura de una nueva Aplicación Web. Me estoy refiriendo a la **adaptación del contenido al dispositivo** que emplea el usuario para acceder a dicha aplicación, tomando de modo adicional el contexto en el que se desenvuelve.

Cuando me refiero al contexto, principalmente, podemos centrarnos en la orientación del dispositivo, la resolución del mismo, etc...

A lo largo de los últimos años, **ha surgido un nuevo paradigma denominado [Responsive Design][ResponsiveDesign], que podemos traducir como Diseño Sensible**. El planteamiento del Diseño Responsable se basa,  en tener en cuenta el Dispositivo y el contexto que el usuario emplea para acceder al contenido de modo que:

* Dicho contenido se adapte al dispositivo, siendo adaptable a las características del Viewport (espacio donde se muestra el contenido) y **se evita que el usuario deba realizar scroll por nuestras páginas**, impidiendo una experiencia de usuario correcta.
* De modo adicional, también **debe adaptarse al modo de navegación del que dispone el usuario** (si la navegación se va a realizar por teclado, por pantalla táctil, etc...)
* **Evitar la duplicidad de páginas** para dar cábida a todos los dispositivos, de modo que **no entremos en un mantenimiento costoso y pesado**
* Marcar las **bases para la evolución de nuestra Aplicación Web** a nuevos dispositivos, de un modo ágil

>El diseño sensible presenta varios aspectos a tener en cuenta, pero en este articulo vamos a enfocarnos a la gestión de las distintas presentaciones (Layouts) de una Aplicación Web diseñada de este modo, siendo adaptadas al llamado Viewport (espacio en el que la página será presentada en el dispositivo que accede a ella).
Recomiendo la lectura, para aquellos que se encuentren cómodos con el ingles, [del post de Ethan Marcotte][ArticuloResponsiveDesign]

# Distintos clientes, misma necesidad
Actualmente, nos encontramos con la siguiente necesidad.

![Necesidad actual: representar contenido adaptado al dispositivo]({{ site.url }}/images/front/responsive/SDR-A1-Layout-Adaptable-Caso.png)


A día de hoy, **nos encontramos con multitud de dispositivos**, que presentan distintas características a las que nuestra Aplicación Web debe tener en cuenta en su diseño:

* A nivel hardware, **las pantallas presentan distintas resoluciones**, en incluso algunos, como las tabletas pueden variarla de modo dinámico.
* Ciertos dispositivos son elegidos por usuarios que requieren desarrollar tareas “sobre la marcha” y de modo óptimo, para mejorar su acceso a Internet, por lo que estamos obligados a **presentarle el contenido más importante de un modo accesible**
* Los dispositivos presentan distintos navegadores, con distinto soporte a lenguajes de marcas y tecnologías complementarias (javascript, soporte a lenguaje de marcas)

# Media Queries, la solución a aplicar
Para ayudarnos en esta nueva tarea, disponemos de un mecanismo denominado [Media Queries][MediaQueries]. El objetivo de esta tecnología, cumple con el objetivo que tenemos que cubrir.

> Si queremos conocer el soporte actual de los navegadores, [podemos encontrar aquí más información][CanIUseMediaQueries].

Por medio del uso de Media Queries, podemos establecer distintas hojas de estilo para lograr que nuestro ntenido se adapte a distintos tipos de medios. Si a este nivel equiparamos los distintos “tipos de medios” a los distintos tipos de dispositivos para los que deseamos que nuestra Aplicación Web, nos encontramos con el siguiente escenario:

![Diagrama de clases del ejemplo]({{ site.url }}/images/front/responsive/Responsive-Design-Arquitectura.png)

Ya sea por el medio que sea, análisis de estadísticas de acceso de dispositivos en Internet, por las necesidades de nuestro cliente o de nuestra empresa; hemos decidido que nuestra aplicación va a realizar la adaptación de su contenido a dos tipos de resoluciones:

* **Dispositivos con un ancho de resolución menor de 400 pixeles (px)**, que visualizarán nuestra aplicación con un layout vertical, representando las distintas zonas cada una en una fila.

![Layout menor de 400 px]({{ site.url }}/images/front/responsive/layoutlt400.png)

* **Dispositivos con un ancho de resolución mayor a 400 pixeles (px)**, que visualizarán nuestra aplicación con un layout que ubique el menú ppal a la izquierda del contenido principal.

![Ejemplo para Layout mayor de 400 px]({{ site.url }}/images/front/responsive/layougt400.png)

Los estilos que son comunes, los vamos a definir en una hoja de estilos CSS (base.css), para ser empleada independientemente de la resolución que tenga el dispositivo con el que accede el usuario.

Este enfoque, nos obliga a tener en cuenta a la hora de diseñar nuestra aplicación, de la importancia que tiene la definición de los estilos CSS y el mejor modo de agruparlo.

Como hemos comentado anteriormente, **media Queries nos va a permitir aplicar una hoja de estilos u otra**, dependiendo de las reglas que establezcamos. En nuestro caso, será el ancho mínimo el valor por el cual la CSS correspondiente será empleada.

Siempre queremos dar soporte a cualquier dispositivo, pero debemos tener en cuenta que el uso de media queries puede tener impacto en cuanto al rendimiento de nuestra Aplicación:

* **El navegador evalúa variaciones en el viewport**, que provocar hacer el usuario, como cambio del tamaño de la ventana donde visualiza el contenido o variación en la orientación del dispositivo, redimensionar la ventana del navegador. Por esta razón, debemos establecer un límite a la hora de indicar el número de reglas, con el fin de no penalizar el rendimiento en la respuesta del navegador
* **Limitar los estilos de las hojas para el layout**, sólo para posicionar contenido de nuestra página y no de presentación
* Si los estilos los tenemos en ficheros CSS, hay que tener en cuenta las peticiones que debe realizar el navegador para no sobrepasar el número optimo

> Por norma general, las peticiones de recursos desde nuestra página debería de estar entre 6 y 8, contando con las peticiones para otros recursos, como las imágenes)

# Resumen
Una vez visto el funcionamiento de Media Queries, podemos reconocer una herramienta a tener en cuenta si queremos adaptar la presentación del contenido de nuestras Aplicaciones Web a los distintos dispositivos que pueden emplear nuestros usuarios, y los que puedan aparecer en un futuro (más que próximo).

A la hora de aplicar Media Queries debemos tener en cuenta:

* El rendimiento. Hay que tener en cuenta que la modularización que supone su uso, implica añadir peticiones de nuestras páginas. Deberíamos tener siempre como meta, que no se superen las 8 peticiones por página, sobre todo si nuestros usuarios van a acceder con dispositivos móviles.
* Los estilos a incluir en las hojas de estilos. Debido a que el navegador reevalua cualquier cambio en el espacio donde se presenta nuestra página, el hecho de añadir cambios en la presentación de los elementos de nuestra página supone más tiempo de proceso del navegador para aplicarlos. Deberíamos, por tanto, añadir a las hojas de estilo cambios en la disposición de los elementos, e intentar centralizar en una hoja base la presentación de los mismos (color de fondo, fuentes, bordes, etc.)

# Herramientas empleadas
Debido a mi “afición” al software libre, me siento obligado a enumerar las herramientas que he empleado para la realización de este artículo:

* Diagramas. Para los diagramas, he empleado la herramienta [DIA][DIA]. Se puede descargar e instalar desde los repositorios por defecto, en Ubuntu.
* Imágenes. Todas las imágenes han sido redimensionadas con [Gimp][Gimp].

[ResponsiveDesign]: http://en.wikipedia.org/wiki/Responsive_Web_Design
[ArticuloResponsiveDesign]: http://www.alistapart.com/articles/responsive-web-design/
[MediaQueries]: http://www.w3.org/TR/2012/REC-css3-mediaqueries-20120619/
[CanIUseMediaQueries]: http://caniuse.com/css-mediaqueries
[DIA]: http://projects.gnome.org/dia
[Gimp]: http://www.gimp.org/
