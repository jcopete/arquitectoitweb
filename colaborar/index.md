---
layout: page
title: Colaborar
excerpt: "Cómo puedes colaborar con Arquitecto IT contribuyendo con tu contenido."
image:
  feature: portada.png
---

[Arquitecto IT][ArquitectoIT] es una página **abierta a cualquier tipo de colaboración**. Siempre que esta verse sobre un **tema de arquitectura tecnológica y lo afrente de la manera más pedagógica posible**.

Si quieres colaborar con [Arquitecto IT][ArquitectoIT] simplemente tienes que realizar los siguientes pasos:

# 1. Trabaja con el Repositorio Git
En [Arquitecto IT][ArquitectoIT] trabajamos con un repositorio Git que puedes encontrar en [https://github.com/arquitectoit/arquitectoit](https://github.com/arquitectoit/arquitectoit). Así lo primero que tienes que hacer es [crearte un fork de dicho respositorio][Fork].


## 1.1. Ubicar el Artículo
El artículo con el que colabores deberá de estar dentro de la carpeta **_post** y a su vez en la subcarpeta de la temática sobre la que estés escribiendo. Por ejemplo **api-management**, **cloud**, **bigdata**,... Si no encuentras la temática más adecuada puedes crear una subcarpeta con dica temática.

## 1.2. Formato del Artículo
El formato del artículo debe de ser **markdown** y su nombre debe de seguir la siguiente estructura:

~~~
YYYY-MM-DD-nombre-entre-guiones.md
~~~

Lo mejor es que eches un ojo a los artículos que hay en la carpeta **_post** para ver cómo darle formato.

## 1.3. MetaInformación del Artículo
En la parte superior del artículo deberás de indicar la metainformación del mismo. Para ello deberás de rellenar los siguientes campos:

~~~
---
layout: post
title: Título del Artículo
excerpt: Resumen del Artículo
categories: Categoría del Artículo. Solo asignale una.
tags: [etiqueta1,etiqueta2,...] Intenta no utilizar muchas
image:
  feature: Fichero con la imagen de cabecera. Debe de ser 1024x256. No se admite otro tamaño.
  credit: Nombre del propietario de la foto. Si existe.
  creditlink: URL del propietario de la foto. Si existe.
comments: true
share: true
author: Tu nombre de usuario (*) Explicado en el punto 2.
---
~~~

## 1.4. Imágenes del Artículo
Si utilizas imágenes dentro de tu artículo puedes ponerlas dentro de la carpeta general **/images**. Dentro de esta carpeta verás que existen diferentes carpetas por categoría dónde alojar tus imágenes.

> Los formatos de las imágenes deben de ser **jpg** o **png**. Recuerda pasarlas por un compresor como [TinyPNG][TinyPNG] antes de subirlas

Para la imagen de cabecera deberás de utilizar una imagen de **1024x256**. Esta imagen deberás de inclurila en la carpeta **/images/covers** del directorio raíz. Si no encuentras una imagen de cabecera, nosotros se la asignaremos.

# 2. Crea tu perfil de Arquitecto
Si es la primera vez que contribuyes con [Arquitecto IT][ArquitectoIT] debes de **crear tu perfil de arquitecto**.

Para ello deberás de completar la información que hay en el fichero **_data/authors.yml**. Sobre el que puedes añadir el siguiente contenido:

~~~
nick_arquitecto:
  name: Nombre real
  email: email
  uri: URL de tu web
  bio: "Descripción del arquitecto"
  avatar: URL de la imagen o nombre del fichero a incluir en /images/arquitectos
  twitter: Usuario Twitter
  linkedin: Usuario LinkedIn
  youtube: Usuario Youtube
  instagram: Usuario Instagram
  facebook: Usuario Facebook
  github: Usuario Git
  lastfm: Usuario LastFm
  flickr: Usuario Flickr
  google:
    plus: Usuario Google Plus
~~~

Rellena solo aquellos que quieras publicar. Solo son obligatorios el **nick_arquitecto, name y bio**.

Si utilizas una foto deberás de incluirla en el directorio **/images/authors/**.

# 3. Publicar el Artículo
Una vez tengas el artículo en tu repositorio, colaborar es tan sencillo como [realizar un pull request sobre nuestra rama de desarrollo][PullRequest].

Y no te preocupes, revisaremos el contenido, formato y demás para ayudarte con tu colaboración.

Si tienes alguna duda puedes [contactar con nosotros][contactar].

[ArquitectoIT]: {{ site.url }}/acerca-de
[Fork]: https://github.com/arquitectoit/arquitectoit#fork-destination-box
[PullRequest]: https://github.com/arquitectoit/arquitectoit/pull/new/dev
[TinyPNG]: https://tinypng.com/
[Contactar]: {{ site.url }}/contactar
