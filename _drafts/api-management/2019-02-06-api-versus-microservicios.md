---
layout: post
title: API versus Microservicios
excerpt: "bla bla"
categories: api-management
tags: [api-management, microservicios]
image:
  feature: covers/api.png
comments: true
share: true
author: victor_cuervo
---

> Qué es un API, qué es un microservicio y qué diferencia hay entre ellos.
Ya hay una definición de Microservicio, quizás se necesite una de API??


Muchas empresas están metidas en procesos de definición de una arquitectura de APIs a la vez que se están definiendo arquitecturas de microservicios. Pero, ¿qué relación hay entre ellos? ¿Es lo mismo un API que es un microservicio? ¿Son cosas antagónicas o complementarias?

En algunos casos los terminos se utilizan de forma intercambiable, siendo correcto una de las veces, pero otras no.

Veamos un poco en detalle que es un API versus Microservicios.

## Qué es un API

**API** es el acrónimo de **Application Programming Interface**, los API son mecanismos de comunicación entre aplicaciones.

Aunque hay muchos sitios dónde podamos definir un API para la comunicación entre aplicaciones, la palabra **API** haría referencia a lo que conocemos como **API Web**

El **API** es una forma de exponer la funcionalidad o unos datos de una aplicación para que sea consumida por un tercero.

Los API suelen tener una definición estándar independiente de la implementación que de la funcionalidad. Esta definicióne estándar se realiza mediante [Swagger][Swagger] (ahora **Open API**).

Para exponer una API tenemos varias formas, las más utilizadas en el mercado son [REST][REST] y [GraphQL][GrapQL]. Aunque hay algunas más modenas como [gRCP][RCP] u otras que se están dejando de utilizar como [SOAP][SOAP]



[Leer más sobre API...][QueEsAPI]


## Qué es un Microservicio

Es un servicio dentro de una arquitectura de microservicios
Son una forma alternativa a la hora de contruir aplicaciones. La idea es hacer aplicaciones que no sean monolíticas y pasasar a construir servicios más pequeños e independientes.

Por lo tanto son **un patrón para construir aplicaciones**
Las aplicaciones se diseñan con servicios con un grado pequeño de acoplamiento para que puedan tener una vida en desarrollo y despliegue independiente, mejorando los tiempos de desarrollo y mantenimiento. Cumplen una funcionalidad, pero cada microservicio puede estar desarrollado con una tecnología diferente, aprovechando las capacidades de las tecnologías en el microservicio concreto.

Al contrario de las aplicaciones monolíticas en las que un cambio afecta a toda la aplicación y dónde la tecnología se comparte entre todas las funcionalidades. Perdiendo las especificidades de ciertas tecnologías para construir funcionalidades.

Por ejemplo si una funcionalidad se adapta más a un modelo NOSQL, no tienes por qué reutilizar la BD relacional general de la aplicación.


Además la división en pequeñas funcionalidades tiene un impacto en las organizaciones de las empresas ya que se trabaja de unas forma vertical sobre la funcionalida y por ende nos permite el dividir dichas funcionalidades en equipos.

[Leer más sobre microservicios...][QueSonMicroservicios]


## Diferencias entre microservicios/api

FUNCIONALIDAD
* Los microservicios son un patrón para construir aplicaciones, mientras que el API sirve para exponer funcionalidad de negocio e integrar aplicaciones.

LENGUAJES
* Los microservicios están implementados en los lenguajes de programación tipo [Java][Java], [.Net][.Net], [Node.js][Node.js],... mientras que los APis son interfaces definidos por [Swagger][Swagger].

FINALIDAD
* Los microservicios tienen como finalidad el implementar una funcionalidad de negocio, mientras que el API principalmente es exponer el negocio, por si se puede monetizar.


## Confluencia entre microservicios/api

* Un microservicio expondrá su funcionalidad mediante un interface REST que puede ser publicado como microservicios.

(poner dibujo)

* un microservicio puede consumir un API. Ojo, esto solo para microservicios que implementen funcionalidad de negocio complejas

(poner dibujo)

* Los microservicios necesitan de los APIs para poder trabajar con esa división por estos mecanismos de exposición y consumo.











[QueSonMicroservicios]: {{site.url}}/microservicios/que-son-los-microservicios/
[QueEsAPI]:
[Swagger]:
[REST]:
[GraphQL]:
