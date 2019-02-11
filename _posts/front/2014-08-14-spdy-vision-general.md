---
layout: post
title: SPDY. Visión General.
excerpt: "Hace no mucho participaba en una conversación sobre los nuevos modelos de desarrollo de software. Equipos ágiles y autosuficientes, con capacidad de decisión a la hora de crear y desplegar su software"
modified: 2014-08-14T23:27:32.066+01:00
categories: front
tags: [spdy, http2]
image:
  feature: covers/spdy.jpg
comments: true
share: true
author: jose_carlos_ferreiro
redirect_from:
 - /navegadores/spdy-vision-general/
---

# ¿Qué es SPDY?
En noviembre de 2009, Google, dentro de su proyecto [Let's make the web faster][WebFaster], anuncia la creación de un nuevo protocolo cuyo principal objetivo es reducir el tiempo de carga de las páginas web. El nombre elegido para el nuevo protocolo es [(pronunciado <em>Speedy</em>)][spdy].

Conjuntamente con el anuncio, se presenta la documentación, la implementación y los resultados de las primeras pruebas realizadas en los laboratorios: **¡la carga de páginas web se ve mejorada en un 55%!** Atendiendo a estos resultados y teniendo en cuenta que son pruebas de laboratorio se puede decir que  el tiempo necesario para visualizar una web se ve reducido, aproximadamente, a la mitad.

# Características
SPDY está diseñado específicamente para **minimizar la latencia de red** y **disminuir el tiempo utilizado en el transporte** de información en las comunicaciones web.

SPDY se sitúa <em>a medio camino</em> entre la capa de sesión y la capa de aplicación. Este protocolo no sustituye al protocolo HTTP sino que lo complementa y mejora determinados aspectos que HTTP no contempla.

![SPDY OSI]({{ site.url }}/images/front/browsers/spdy_osi.jpg){:class="img-responsive"}

Las características principales en las que se basa SPDY:

* **Conexiones multiplexadas**: es la idea base del protocolo. Se permite un número ilimitado de peticiones sobre una misma conexión. Esta característica también mejora la eficiencia del protocolo TCP: se necesita realizar menos conexiones y enviar menos paquetes de información en cada conexión (aunque son más densos).
* **Compresión de cabeceras HTTP**: SPDY comprime las cabeceras HTTP, tanto de peticiones como de respuestas. Esto hace que se envíen menos paquetes y menos bytes en cada paquete disminuyendo el tiempo necesario para procesar la petición.
* **Priorización de peticiones**: SPDY implementa un sistema de prioridades para el procesamiento de peticiones. El cliente puede asignar a cada petición que realiza una prioridad y el servidor resolverá antes las peticiones de prioridad más alta. Esto previene que se produzca una congestión de red con peticiones a recursos que no son críticos.
* **<em>Push</em> desde el servidor**: este protocolo experimenta con la idea de enviar datos desde el servidor al cliente antes de que este haga una petición expresa a un recurso, es decir, el servidor envía información al cliente que este va a necesitar pero que aún no ha pedido. Para ello utiliza la cabecera <em>X-Associated-Content</em>. Esta característica puede suponer una mejora significativa en el tiempo inicial de carga de páginas web.


# Uso de SDPY
Actualmente, está liberada la <a title="Draft 3 SPDY" href="http://dev.chromium.org/spdy/spdy-protocol/spdy-protocol-draft3" target="_blank">versión 3 de SPDY</a>. Para poder sacar partido a las características del protocolo y aprovechar las mejoras en el rendimiento de las comunicaciones web es necesaria una adaptación de las dos partes más importantes implicadas en la comunicación web: el navegador y el servidor.

Del grupo de navegadores más conocidos y utilizados, Internet Explorer, Chrome, Firefox, Opera y Safari, los que soportan SPDY son Chrome y Firefox desde las versiones 6 y 11, respectivamente. También en sus versiones para Android.** <a title="Uso de navegadores" href="http://gs.statcounter.com/#browser-ww-monthly-201202-201207-bar" target="_blank">Esto supone más de la mitad de los navegadores que se utilizan actualmente en la navegación por internet</a> **por lo que ya existe un uso muy alto de navegadores web que pueden aprovechar las mejoras proporcionadas por SPDY. Amazon con Silk, el navegador para Kindle, también soporta SPDY.

Opera, por su parte, ha lanzado un cliente a través de Opera Labs con una versión de prueba que soporta SPDY pero aún no está disponible en la versión estable de su navegador, aunque probablemente lo estará en una de las siguientes versiones estables.

Por otro lado, dos compañías muy importantes en el mercado de navegadores como Microsoft y Apple, con sus navegadores Internet Explorer y Safari respectivamente, no parecen tener planes para dar soporte a SPDY.

Si quieres puedes <a title="Consultar soporte SPDY de tu navegador" href="http://caniuse.com/#feat=spdy">consultar el soporte de los navegadores para SPDY</a>.

El otro agente principal involucrado en las comunicaciones web son los servidores web. Google es quien más esfuerzo está realizando para que el proyecto salga adelante dando soporte a este protocolo en todos sus servicios que funcionan bajo HTTPS: Google Search, Gmail, Google Ad’s…

Recientemente, Twitter y Facebook también han anunciando que dan soporte a SPDY en sus servidores, es decir, van a servir sus páginas web a través de este protocolo si el usuario accede con un navegador que lo soporte. Varios servidores web muy utilizados van implementando, poco a poco, el soporte a SPDY: el módulo <em><a title="mod_spdy - Módulo de Apache para soportar SPDY" href="http://code.google.com/p/mod-spdy/" target="_blank">mod_spdy</a></em> da soporte a este protocolo para el servidor Apache y también <em><a title="Jetty" href="http://jetty.codehaus.org/jetty/" target="_blank">Jetty</a></em> y <a title="nginx" href="http://nginx.org/" target="_blank">nginx</a> implementan las características para soportar SPDY.

Aunque hablamos de que es necesaria una adaptación tanto de los navegadores como de los servidores para utilizar SPDY, estas adaptaciones son transparentes a los usuarios de la web. Es posible que las mejoras introducidas por este protocolo vayan a influir en el diseño de los nuevos sitios web y en las técnicas de optimización de la parte de <em>front-end</em> de los servicios que proporcione una empresa si se incrementa o estandariza el uso de este protocolo.


# Conclusiones
El objetivo inicial de SPDY era **proporcionar un acceso más rápido a la web sin necesidad de cambiar el contenido y de forma transparente a los usuarios**. Ha demostrado que es posible y viable. Presenta importantes mejoras a nivel de rendimiento en cualquier tipo de conexión,  tanto en conexiones normales como en conexiones para móviles.

SPDY se basa en una serie de buenas ideas (compresión de cabeceras, una única conexión para múltiples peticiones, etc.) que dan una base sólida para la posible definición de un nuevo estándar. <a title="Propuestas HTTP 2.0" href="http://trac.tools.ietf.org/wg/httpbis/trac/wiki/Http2Proposals" target="_blank">¿HTTP 2.0?</a>

**SPDY es una de las propuestas, enviada por Google al IETF, para la definición del estándar HTTP 2.0**. Otra de las propuestas enviada por Microsoft es <a title="HTTP Speed+Mobility" href="http://blogs.msdn.com/b/interoperability/archive/2012/03/25/speed-and-mobility-an-approach-for-http-2-0-to-make-mobile-apps-and-the-web-faster.aspx" target="_blank">HTTP Speed+Mobility</a> y, para su definición, toma como base varias características de SPDY y añade mejoras relacionadas con el trabajo que se ha hecho hasta ahora de WebSockets.

En esta época donde existe una gran cantidad de información y la posibilidad de acceder a ella desde cualquier punto y dispositivo es imprescindible que el acceso sea lo más rápido posible. Parece que Google y SPDY han iniciado con fuerza este proceso de mejorar el acceso a la información de la red.

Estaremos atentos a los movimientos que se vayan produciendo. Mientras tanto, ¿cuál es vuestra opinión sobre este protocolo? ¿Creéis que su uso se va a seguir extendiendo? ¿Se convertirá en un estándar <em>de facto</em>?

[WebFaster]: https://developers.google.com/speed/?hl=es "Let's make the web faster"
[spdy]: http://dev.chromium.org/spdy "SPDY"
