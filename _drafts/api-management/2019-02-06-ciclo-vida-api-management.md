---
layout: post
title: Ciclo de Vida del API
excerpt: "bla bla"
categories: api-management
tags: [api-management]
image:
  feature: covers/api.png
comments: true
share: true
author: victor_cuervo
---

Cuando hablamos del **ciclo de vida del API** estamos hablando de las siguientes 5 fases:

1. Concepción
2. Diseño
3. Desarrollo
4. Mantenimiento
5. Deprecación

## Concepción
La primera pregunta que nos debemos de hacer en la **fase de concepción** de un API es *¿Realmente necesito un API?*

En la **fase de concepción** se tiene que validar que lo que nos están pidiendo es realmente un API y que no es otro tipo de solución de software, ya que muchas veces pensamos que todo se tiene que resolver creando un API. La idea de crear un API es la de **exponer una funcionalidad clara de negocio**, bien sea para ser consumida de forma interna por la organización o bien consumida por una entidad externa y en este caso, incluso monetizarla.

En la **fase de concecpión** es dónd describimos de forma generar las funcionalidades que buscamos con nuestro API. Tenemos que saber exactamente la funcionalidad de negocio que queremos exponer por el API, qué tipo de audiencia va a tener el API, si lo vamos a monetizar o no,...

Deberán de **definirse casos de uso** que serán los que se detallen a continuación en la **fase de diseño** y que se implementen en la **fase de construcción**.

## Diseño
El API empieza a tomar forma. La idea es que las funcionalidades que se han definido en la **fase de concepción** se aterricen y se definan mediante el estándar [Swagger][Swagger] (Open API) u [GraphQL][GraphQL].

La idea es que **se definan las entidades** que va a manejar, así como **las operaciones** sobre dichas entidades. Cada uno de los end-point debe de tener una **descripción clara sobre la funcionalidad que aporta**.

Además hay que **crear los juegos de pruebas** sobre las operaciones que hemos definido en las que se incluyan peticiones y respuestas de ejemplo. Para ello nos podemos apoyar en herramientas como [Postman][Postman]. Los ejemplos de peticiones y respuestas deben dar respuesta a los casos de uso de la **fase de concepción**.

Adicionalmente, en esta **fase de diseño** se deberá de adjuntar *mockups o sandbox* para poder probar los APIs por parte de los futuros consumidores, sin la necesidad de que tengamos construido y disponible nuestro API. De esta forma podemos acelerar mucho la creación de las aplicaciones alrededor de nuestro API.

## Desarrollo
Una vez tenemos el API diseñado pasamos a la **fase de desarrollo**. Aunque en algunas ocasiones queramos empezar directamente por esta **fase de desarrollo** no debemos de menospreciar las **fases de concepción** y **diseño** ya que un buen trabajo en esas fases hará que el desarrollo sea más ligero.

En la **fase de desarrollo** utilizaremos la definición realizada en los documentos [Swagger][Swagger] para comenzar con la codificación en el lenguaje de programación que utilicemos para la implementación del API.

Pueden aparecer algunos detalles técnicos en esta fase que no estén resueltos como pueden ser la gestión de ciertos tipos de datos, la cual se puede quedar en un mero tema de formato de los tipos o puede llegar a ser hasta una carencia funcional de nuestro API.

Es muy importante la calidad del código a la hora de desarrollar el API, ya que carencias de calidad harán que la siguiente **fase de mantenimiento** sea más o menos costosa.

## Mantenimiento
Una vez que completemos el desarrollo de API y tengamos el *API en producción* pasaremos a la **fase de mantenimiento**. La vida útil de un API dependerá de cuanto tiempo este API cubra una necesidad de negocio.

En esta fase hay que focalizarse en *monitorizar el API*. Es decir, ver cómo se está comportando y si está generando errores. Cuando hablamos de *monitorización de API* nos referimos a lo que es la *monitorización externa* sobre cómo se está comportando el API desde el punto de vista del cliente y de la *monitorización interna*, cómo se comporta la implementación del API en los servidores y bases de datos que lo sustentan.

Esta *monitorización del API* hará que vayamos mejorando el propio API con el paso del tiempo en esta **fase de mantenimiento**.

## Deprecación
En algún momento de la vida del API este llegará a su **fase de deprecación**. Esto sucedería cuando ya no existe utilidad del API para los clientes. Este momento de retirada del API no tiene que ser porque ya no sea necesaria la funcionalidad, suele suceder más cuando han aparecido nuevas *versiones del API* o nuevos API que nos ofrecen mayor funcionalidad.

Llegado el momento de esta **fase de deprecación** deberemos de **notificar a todos los clientes que están subscritos al API que este va a ser retirado**. Esta notificación deberá de realizarse con el suficiente tiempo como para que los consumidores del API puedan adaptar sus desarrollos al nuevo API o para que retiren la invocación.

En esta notificación se suele incorporar el *Path* de la nueva versión o de la nueva API, para facilitar a los consumidores su adaptación.


[Swagger]:
[GraphQL]:
[Postman]:
