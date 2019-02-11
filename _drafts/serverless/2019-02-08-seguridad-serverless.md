---
layout: post
title: Seguridad Serverless
excerpt: "bla bla bla"
categories: serverless
image:
tags: [serverless]
  feature: covers/dialogflow.jpg
comments: true
share: true
author: victor_cuervo
---



Securizar una aplicación Serverless es diferente a securizar una aplicación monolítica tradicional.

En el caso de la seguridad de modelos serverless hay que focalizarse en la seguridad del código. Ya que los riesgos potenciales van enfocados a la lógica de aplicación.

Es por ello que hay que cuidar que no haya inyecciones de código. En este caso se puede optar por recubrir los servicios para establecer este control y no delegarlo sobre el desarrollador.

Otro punto importante es el control de accesos. Es decir, quién es el usuario que puede acceder y cual no. Se pueden utilizar sistemas como Vanadium - https://vanadium.github.io/core.html


Además hay que añadir un servicio de monitorización de forma "obligatoria". De esta manera podremos analizar eventos que no sean eventos predefinidos por la lógica de la aplicación.


Se resume en:

* Calidad de Código
* Control de Acceso a los Servicios
* Monitorización
