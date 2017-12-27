---
layout: post
title: El reto de monitorizar microservicios
excerpt: "Análisis de los retos en la monitorización de microservicios según  Adrian Cockcroft."
categories: microservicios
tags: [monitorización, microservicios]
image:
  feature: covers/monitoring.jpg
comments: true
share: true
author: victor_cuervo
---

Interesante charla de [Adrian Cockcroft][AdrianCockcroft] sobre **El reto de Monitorizar Microservicios (Monitoring Microservices: A challenge!)**

[Adrian Cockcroft][AdrianCockcroft] incide en que la propia definición de un microservicio "Loosely coupled service oriented architecture with bounded context" nos da dos de los puntos a tener en cuenta a la hora de monitorizar microservicios. Y es que al ser ligeramente acoplados y al tener su contexto acotado tendremos muchos microservicios que tendrán alguna relación entre sí.

En la monitorización de servicios serán importantes:

**1. Velocidad** - venimos desde datacenters que son auténticos silos, dónde se despliega en meses aplicaciones para toda la vida, pasando por entornos virtualizados, gestión de contenedores para hacer pruebas de test que duran minutos llegando al extremos de entornos que viven milisegundos para ejecutar un paso de un proceso como sucede en los entornos AWS Lambda Events.

**2. Escalado**, como crecer en máquinas para estos entornos tan altamente demandantes. ¿Cómo podemos saber qué uso de CPU tienen nuestros microservicios y cuanta demanda existe?

**3. Flujo de los microservicios**, se deberá de conocer el flujo de los microservicios. Pero dada la cantidad de microservicios que existen se generarán gráficos como el siguiente:

![Monitorización de Microservicios]({{ site.url }}/images/microservicios/MonitorizacionMicroServicios.jpg)

**4. Fallos**, como definir una tolerancia a fallos y controlar las caídas de regiones de microservicios en nuestro sistema.

**5. Testing**, cómo realizar testing sobre los sistemas, sin que estas pruebas de test y simulación sean muy caras.

**6. Simulación**, cómo se pueden simular los diferentes tipos de arquitecturas de microservicios a tener y ver cual sería su comportamiento.

Para este diseño de los flujos, pruebas de test, detección de fallos en arquitecturas de microservicios, [Adrian Cockcroft][AdrianCockcroft]> ha creado [la herramienta Spigo][Spigo], la cual nos ayudará en la definición de este tipo de arquitecturas.

No os perdáis el vídeo sobre **El reto de Monitorizar Microservicios<em> (Monitoring Microservices: A challenge!)</em>**

<iframe width="560" height="315" src="https://www.youtube.com/embed/smEuX-Hq6RI" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>

Además os dejo la presentación que iba realizando:

<iframe src="//www.slideshare.net/slideshow/embed_code/key/nzKVKFKOt02ToD" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/adriancockcroft/software-architecture-monitoring-microservices-a-challenge" title="Software Architecture Conference - Monitoring Microservices - A Challenge" target="_blank">Software Architecture Conference - Monitoring Microservices - A Challenge</a> </strong> from <strong><a href="https://www.slideshare.net/adriancockcroft" target="_blank">Adrian Cockcroft</a></strong> </div>


[AdrianCockcroft]: https://twitter.com/adrianco
[Spigo]: https://github.com/adrianco/spigo
