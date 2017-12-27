---
layout: post
title: Ejemplo de Layout Adaptable con Media Queries
excerpt: "Ejemplo de una página que va a adaptar su presentación de acuerdo al ancho del dispositivo que accede a ella."
categories: front
tags: [responsive design, media queries, accesibilidad]
image:
  feature: covers/responsive.png
comments: true
share: true
author: juan_manuel_garcia
---

# Ejemplo de Diseño Sensible

Para el desarrollo de este ejemplo, [tomamos el caso descrito en mi anterior articulo a modo de diseño][LayoutAdaptable]. De este modo, tenemos una página **que va a adaptar su presentación de acuerdo al ancho del dispositivo que accede a ella**.

Este es el Diagrama de Componentes de nuestro ejemplo:

![Diagrama de clases del ejemplo]({{ site.url }}/images/front/responsive/Responsive-Design-Arquitectura.png)

> Los estilos que son comunes, los vamos a definir en una hoja de estilos CSS (base.css), para ser empleada independientemente de la resolución que tenga el dispositivo con el que accede el usuario.

Como se puede observar en el diagrama, hemos decidido que nuestra aplicación **va a realizar la adaptación de su contenido a dos tipos de resoluciones**:

* Dispositivos con un ancho de **resolución menor de 400 pixeles (px)**, que visualizarán nuestra aplicación con un layout vertical, representando las distintas zonas cada una en una fila

![Layout menor de 400 px]({{ site.url }}/images/front/responsive/layoutlt400.png)

* Dispositivos con un ancho de **resolución mayor a 400 pixeles (px)**, que visualizarán nuestra aplicación con un layout que ubique el menú ppal a la izquierda del contenido principal

![Ejemplo para Layout mayor de 400 px]({{ site.url }}/images/front/responsive/layougt400.png)

>Este modo nos va a permitir, el soporte incluso para el mismo usuario en el caso que disponga de un dispositivo con el que pueda variar su orientación

Con el fin de comprobar el cambio en dicha página, la cabecera de dicha página cambiará de color como consecuencia del ancho del dispositivo que accede.

[Puedes ver el funcionamiento del ejemplo que vamos a realizar][EjemploArticulo].

# Áreas de la Pagina y su comportamiento

Nuestro ejemplo, presenta las siguientes secciones:

* Una sección que es la cabecera del sitio
* Una barra de menu, con enlaces a otras secciones.
* Una sección, donde los articulos son presentados
* Un pie de página, con un enlace para contactar con el creador de la página

Los cámbios que se van producir son los siguiente:

## Dispositivos con un máximo de 400 px
En este caso, las distintas secciones se presentan de modo lineal, una tras la otra. La hoja de estilos, con el nombre **Adaptlt400.css**, dispone de los siguientes estilos:

~~~css
#banner {
  color: black;
  font-size: 1em;
  text-align: center;
  background-color:white;
}
~~~

En este caso, como no queremos alterar las disposiciones de los elementos, cambiamos el color de fondo de la cabecera, a

## Dispositivos con un mínimo de 400px
Los dispositivos que cumplan con esta característica, reciben distinta presentación:

*	La barra de menú se presenta a la izquierda, alineando los distintos enlaces
*	La sección con el contenido, se presenta a la derecha del menú

Para conseguir ese efecto, creamos la hoja **Adaptgt400.css**, con los siguientes cambios:

Cambiamos los elementos del menú de navegación, para se presenten como una lista

~~~css
ul {
  text-align: left;
  list-style-type: none;
  padding: 0;
  margin: 0;
}
li {
  display: block;
}
#banner {
  color: white;
  font-size: 1em;
  text-align: center;
  background-color:blue;
}
~~~

Indicamos que queremos que la barra de navegación **se ubique a la izquierda de la zona de contenidos**.

~~~css
#navMenu {
  padding: 0;
  display: block;
  float:left;
  width: 20%;
  height: 100%;
}
~~~

Indicamos que la sección con los artículos, también flote sobre el menú de navegación.

~~~css
#workArea {
  float:left;
  width: 80%;
}
~~~

# Aplicar Media Queries a la página
Para que se aplique la hoja de estilo correspondiente, debemos incluir en nuestra página el enlace a las hojas de estilos.

Para ello, empleamos la etiqueta “link”, añadiendo las dos hojas de estilos:

~~~html
<!-- Estilos-->
<link rel="stylesheet" href="./css/base.css" type="text/css" />
<link rel="stylesheet" type="text/css" href="./css/Adaptlt400.css" media=" (max-width: 400px)" />
<link rel="stylesheet" type="text/css" href="./css/Adaptgt400.css" media=" (min-width: 400px)" />
<!-- Fin Estilos-->
~~~

Como se observa, a primera vista, tenemos un nuevo atributo “media” que es el que vamos a emplear para indicar cuando se debe aplicar cada una de las hojas de estilos.

# Herramientas empleadas
Debido a mi “afición” al software libre, me siento obligado a enumerar las herramientas que he empleado para la realización de este artículo:


*	**Diagramas**. Para los diagramas, he empleado la herramienta [DIA][DIA]. Se puede descargar e instalar desde los repositorios por defecto, en Ubuntu.
* **Imágenes**. Todas las imágenes han sido redimensionadas con [Gimp][Gimp].
*	**Desarrollo HTML 5**. Para el desarrollo de la página, he empleado [BlueGriffon][BlueGriffon].

[LayoutAdaptable]: {{ site.url }}/front/layout-adaptable-en-disenos-sensibles/
[EjemploArticulo]: http://garciamanzanero.eu5.org/ArquitectoIt/DSArticulo1/DSEjemploArticulo1.xhtml
[DIA]: http://projects.gnome.org/dia/
[BlueGriffon]: http://bluegriffon.org/
[Gimp]: http://www.gimp.org/
