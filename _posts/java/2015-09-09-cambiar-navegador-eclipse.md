---
layout: post
title: Cambiar el navegador en Eclipse
excerpt: "Cómo poder configurar el navegador por defecto en la herramienta de desarrollo Eclipse"
categories: java
tags: [eclipse]
image:
  feature: covers/eclipse.jpg
comments: true
share: true
author: victor_cuervo
---

Eclipse viene con un navegador interno por defecto el cual no tiene muchas de las funcionalidades de los últimos navegadores. Así que si estás probando alguna cosa sobre los nuevos APIs de [HTML5][HTML5] o funcionalidades como [CSS3][CSS] este navegador no te va a ser de utilidad.

Es por ello que lo mejor es cambiar el navegador en Eclipse e indicarle que cuando visualicemos algún contenido web nos cargue uno de los navegadores que tengamos instalados en nuestro ordenador. Ya sea Chrome, Opera, Safari,... Y de esta forma poder probar de forma correcta nuestro desarrollo.

Si quieres cambiar el navegador en Eclipse lo primero que deberás de hacer es ir al **menú de preferencias**. Una vez que estés en el **menú de preferencias** deberás de ir a la opción <kbd>General >> Web Browser</kbd>

![Cambiar Navegador en Eclipse]({{ site.url}}/images/java/eclipse/eclipse_webbrowser.jpg)

En este menú verás que puedes seleccionar que se ejecute el navegador por defecto del sistema o elegir uno de los navegadores que tengas instalados. En este caso deberás de elegir la opción "Use External Web Browser".

En la lista suelen estar los navegadores externos que estén en el sistema. En el caso de que no aparezca un navegador siempre puedes añadirlo mediante el botón <kbd>New..</kbd> y localizarlo en su directorio.

Así que recuerda, si eres un desarrollador web y utilizas Eclipse como plataforma, es muy recomendable que pienses en cambiar el navegador en Eclipse.

[HTML5]: http://www.manualweb.net/html5/
[CSS]: http://www.manualweb.net/css/
