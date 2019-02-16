---
layout: post
title: Breve introducción a OpenID Connect
excerpt: "Introducción a OpenID Connect, ventajas y casos de uso de este protocolo de autenticación."
categories: api-management
tags: [OIDC]
image:
  feature: covers/online-identity.png
comments: true
share: true
author: joaquin_copete
---

[OpenID][oid] nace como un estándar de autenticación descentralizado, y durante años sus diferentes desarrollos corrieron en paralelo a los de un estándar de authorización llamado OAuth. Con el desarrollo de OpenID Connect, 2014, se fusionan ambos mundos y OpenID Connect se desarrolla sobre el framework de Autorización OAuth 2.0.

# ¿Qué es OpenID Connect?

Por tanto, podemos definir OpenID Connect como un servicio de identidad, que utilizaremos para autenticar a los usuarios finales. Puede ser utilizado en dos direcciones:

* Como proveedores del servicio, somos capaces de garantizar la identidad del usuario y podemos brindar un interfaz de estándar abierto a terceros.
* Como consumidores del servicio, eliminamos la necesidad de mantener y securizar passwords y perfiles de usuario, y podemos centrarnos en ofrecer la funcionalidad de nuestro producto.

Un punto importante a destacar es que OpenID Connect está basado en estándares abiertos, OAuth como mencionaba al principio. Sin necesidad de entrar en los detalles técnicos, pero otro de los beneficios es la existencia de múltiples librerias y módulos que nos ayudarán a acelerar los desarrollos.

# ¿Qué nos ofrece OpenID Connect?

* Nos provee un protocolo estándar para verificar la identidad de un usuario final
* Está basado en estándares abiertos, OAuth, y es independiente de la aplicación o dispositivo. Esto facilita implementaciones e integraciones más sencillas, o con menos esfuerzo.
* Permite el uso de diferentes mecanismos de seguridad, por ejemplo el usuario será autenticado en un gestor de identidades que conoce, si necesidad de nuevos procedimientos de registro o intercambio de contraseñas.
* Permite el intercambio de la información del perfil de usuario. Siempre con el consentimiento del usuario final, y con la cantidad de información que previamente el usuario haya consentido.

# ¿Por qué es OpenID Connect interesante?

Uno de los factores de uso más importantes de OpenID Connect es que está basado en estándares abiertos, es más facil usar **el servicio de un tercero que ya ha implementado el proceso de registro de un usuario y el almacenamiento seguro de sus contraseñas y datos privados**. Además si lo pensamos como usuarios, tampoco queremos rellenar en cada nuevo sitio todos nuestros datos, ¿en cuántas ocasiones no hemos probado un sitio nuevo por no rellenar un formulario gigante? ¿cuánto ha costado a la empresa tener este proceso?

Otro elemento importante a tener en cuenta es que el uso de un protocolo como OpenID Connect no valida inmediatamente una identidad, es decir, aunque algunos  proveedores de identidad como Google o Facebook provean este servicio no tiene porqué ser un servicio confiable. Es siempre más fiable **la información provista por agencias gubernamentales o similares que han validado efectivamente la identidad, y que puede ser utilizada con fines legales**.

Al tener acceso al perfil del usuario esto nos permite agilizar ciertos procesos, pero es fundamental también la capacidad que tenemos para ofrecer el **perfil del usuario segmentado por ámbitos dependiendo del consentimiento del usuario**. Desde el punto de vista técnico, el perfil de usuario se confecciona mediante el uso de unos elementos de información llamados claims, el acceso a más o menos claims estará sujeto al consentimiento de usuario.

Esto nos permite hablar de otro aspecto que hace útil a OpenID Connect, el mayor control que tienen **los usuarios sobre su identidad digital**. Esta identidad puede estar registrada en un único lugar, donde el registro se hace una única vez y pueden tener la posibilidad de reutilizar sus credenciales de identidad en tantos lugares como se permita el login con este proveedor de identidad. De igual forma los usuarios pueden permitir o denegar en cualquier moemnto el uso de su presencia en un único punto, lo que puede ser un beneficio para ellos.

Por último y no menos importante es **minimizar los riesgos de seguridad asociados a las contraseñas**. Uno de los peores hábitos es tener la misma contraseña para diferentes sitios, con lo cual conocida en un sitio, conocida en todos. También ocurre que en diferentes lugares las reglas para la validez de una contraseña son diferentes, su patrón, tiempo de vida, etc. Con OpenID Connect las contraseñas no se van a compartir nunca, y de igual forma el estándar no limita ni define la forma en que el usuario debe ser autenticado, lo cual nos permite que los proveedores de identidad pueden reforzar la seguridad en estos términos tanto como sea necesario con el uso de dobles factores de autenticación, protección de la infraestructura, que es algo en lo que normalmente no nos enfocamos cuando el valor de nuestro sitio es otro distinto.

# ¿Cómo podemos usar OpenID Connect?

Para facilitar la comprensión he creado un video sobre este tema donde puedes aprender a utilizar OpenID Connect, lo puedes encontrar en [A Brief introduction to OIDC][oidc-video].

[oid]: https://openid.net
[oidc]: https://openid.net/connect/
[oidc-video]: https://www.youtube.com/watch?v=kEYLbh9LHzE


