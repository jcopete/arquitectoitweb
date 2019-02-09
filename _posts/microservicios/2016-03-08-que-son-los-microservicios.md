---
layout: post
title: ¿Qué son los Microservicios?
excerpt: "Una de las tendencias en Arquitectura de Software de las que más se viene hablando las últimas fechas son los microservicios. Pero, realmente, ¿qué son los microservicios?"
categories: microservicios
tags: [soa,restfull,microservicios]
image:
  feature: covers/microservicios.png
comments: true
share: true
author: victor_cuervo
redirect_from:
 - /arquitectura/microservicios/que-son-los-microservicios/
---

Una de las tendencias en Arquitectura de Software de las que más se viene hablando las últimas fechas (desde el 2014) son los **microservicios**. Pero, realmente, *¿qué son los microservicios? ¿Qué tiene que ver los microservicios con el SOA? ¿Qué nuevas capacidades nos ofrecen dentro del ámbito del desarrollo de aplicaciones?*

Quizás, para poderlo explicar deberemos de analizar la situación en la que nos encontrábamos del desarrollo del software y cual es el nuevo enfoque.

# Aplicaciones monolíticas y problemas que conllevan
Si pensamos en aplicaciones de software uno de los enfoques de diseño es el de construir **aplicaciones monolíticas**. En este enfoque todo el software que desarrollamos de una aplicación se construye de manera conjunta, apoyándonos sobre diferentes librerías o frameworks y realizando un despliegue masivo de la aplicación.

El diseño de aplicaciones monolíticas trae consigo una serie de problemas o inconvenientes:

* El tiempo invertido en realizar un pequeño cambio y desplegarlo en PRO
* Capacidad de absorber nuevas necesidades en el software que se está desarrollando.
* Ante un cambio, hay que probar toda la aplicación. Hay que tener arrancada toda la aplicación aunque hagas pruebas unitarias.
* Ante un cambio hay que volver a desplegar toda la aplicación y rearrancarla.
* Al ser un solo proceso se ejecuta una sola vez y el escalado deberá de ser detrás de un balanceador que escale de forma horizontal por varias instancias.
* En los circuitos de desarrollo, cambios, despliegue y pruebas queda tan poco tiempo entre release y release que es complejo realizar la gestión de versiones/release llegando a complicar mucho la gestión del software.


> Esto no quiere decir que el desarrollo de aplicaciones monolíticas no sea una solución. Hay casos en los que es una buena opción.

# Nuevas tendencias en el desarrollo del software
Los **microservicios** no han llegado al diseño del software de la noche a la mañana, si no, que hay un conjunto de tendencias que han hecho que el escenario sea favorable.

* Mejora en los procesos de integración continua y despliegue de software
* Consolidación de los API mediante sistemas RESTful como sistemas de integración.
* Necesidad de acometer nuevas tecnologías como el BigData
* El cloud con la disponibilidad de entornos de ejecución autoaprovisionados.
* Implantación de metodologías ágiles, dónde hay un desarrollo dirigido por el usuario en búsqueda de funcionalidad útiles, dentro de un proceso iterativo.
* Abandono paulatino de los enfoques de factoría del desarrollo del software hacía un modelo más artesanal. Menos ingeniería y más creatividad.

# ¿Qué resuelven los Microservicios?

Los **microservicios** no vienen a resolver un nuevo problema, si no que nos ofrecen una forma diferente de enfocar el desarrollo de aplicaciones. La idea que subyace detrás de las arquitecturas de microservicios es el *“divide y vencerás”*. El nuevo modelo plantea dividir la aplicación en pequeñas funcionalidades o servicios para implementar la aplicación.

De esta forma podemos hablar de tres planos de la arquitectura de la aplicación:

## Arquitectura y Desarrollo de la Aplicación
La aplicación se estructurará en un conjunto de servicios independientes entre sí. Cada uno de los servicios debe de cubrir una funcionalidad clara de negocio. Esta independencia y división permite que su implementación en cuanto a código y persistencia de datos pueda ser políglota.

## Gobierno de los Servicios
Los servicios en los que dividamos la aplicación no necesitarán ser gobernados o se aplicará un pequeño gobierno (registro del servicio). Los servicios se comunicarán entre sí mediante protocolos ligeros que no contengan ninguna lógica.

## Despliegue y Ejecución
Cada uno de los servicios se puede desplegar de forma independiente, sin afectar al resto. De esta manera se podrán realizar modificaciones del software aisladas en un menor periodo de tiempo. A la hora de ejecutarse los servicios, estos se ejecutarán en procesos diferentes. Buscando el escalado más adecuado para cada uno de los servicios.

# Definición de los Microservicios

Con todo esto podríamos recurrir para responder a la pregunta de qué son los servicios a la [definición de James Lewis y Martin Fowler][DefincionMicroservicios], la cual nos dice que:

> "Una Arquitectura de Microservicios ofrece un enfoque de desarrollar una aplicación como un **conjunto de pequeños servicios**, mediante un **enfoque políglota de programación** y con **diferente sistemas de almacenamiento**, que **se ejecutan en su propio proceso** y que **se comunican entre sí mediante mecanismos ligeros http/api, sin necesitar tener una gestión centralizada de los mismos**. Los servicios **representan capacidades de negocio** y **son desplegados de forma independiente.**"

[DefincionMicroservicios]: http://martinfowler.com/microservices/#what
