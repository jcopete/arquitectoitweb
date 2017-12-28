# ¿Qué es API Management?

Durante mucho tiempo las empresas han utilizado diferentes formas de compartir información entre sistemas o con empresas externas. A la sazón encontramos a lo largo del tiempo tecnología como los **webservices** o arquitectura completas como **SOA (Service Oriented Architecture)**.

Estos servicios que nos sirven para compartir información presentan una serie de necesidades como son, *el ser gobernados, la gestión como activo de software, sus elementos de seguridad, documentación,...*

No nos engañemos ya que parte de estas necesidades estaban cubiertas en arquitecturas SOA. Si bien, quizás, demasiado orientado al mundo de los desarrolladores o sistemas.

Por otro lado cabe reseñar que la cantidad de dispositivos que se pueden conectar a una empresa ha crecido significativamente en los últimos años. Ya no hablamos de las típicas aplicaciones web o móviles. Estamos hablando de miles de tipos de dispositivos IoT, de sensores, de televisiones, de negocios que nacen de forma transversal a varias empresas,... este nuevo escenario hace que sea mayor la demanda de cómo compartimos información con el exterior.

Y es que uno de los puntos adicionales que se suma en el mundo del **API Management** es la capacidad de gestionar estos servicios de información como un **activo empresarial más**. Es decir, las empresas pueden sacar rédito de dichos activos.

Al pasar, estos servicios, a ser un **activo empresarial** más, deben de tener un componente más de negocio. Dónde usuario del negocio (no usuarios tecnológicos) sean capaces de darles forma, comercializarlos y sacarles rentabilidad.

> De esta manera podemos definir un entorno de **API Management** como aquel proceso que permite al negocio *exponer servicios de información*, *bien documentados* de una *forma segura y escalable*, de tal manera que pueda sacar un *beneficio empresarial*. Para ello se necesitará una *forma de exponer y compartir dichos servicios*, así cómo de *analizar el comportamiento de los mismos*.

Por lo tanto los puntos básicos de diseño que toda estrategia **API Management** debe tener en cuenta son:

* Diseño de los Servicios
* Documentación
* Publicación
* Seguridad
* Analítica
* Escalabilidad

## Diseño de Servicios
Los servicios deben diseñarse de una forma coherente, representando elementos de negocio. Ya que no se nos olvide, la idea es utilizar estos servicios como un activo más. Es por ello que deberemos de huir de diseños orientados a tecnología y los conceptos de negocio deben de reflejarse en el diseño de servicios de una forma clara.

## Documentación
Los APIs deben de estar bien documentados para que se sepa su funcionamiento y cómo interactuar con ellos de una forma independiente.

De esta manera cualquier persona externa a la empresa podría llegar a construir un producto de manera independiente sobre dicho API.

Es una buena práctica en el modelo de documentación acompañarlo con un servicio de testing para que se pueda comprobar diferentes respuestas atendiendo a diferentes peticiones.

## Publicación
Una de los aspectos más importantes en la estrategia de **API Management** es la capacidad de que los servicios de información sean localizados.

Es por ello recomendable la utilización de algún tipo de **portal** para la publicación de estos servicios. Facilitando así su localización y consulta.

## Seguridad
Como punto de acceso a la información de nuestra empresa es importante que se establezca un modelo robusto de seguridad sobre los servicios.

Por lo tanto es necesario que se compruebe que usuarios tienen acceso a los recursos y bajo que circunstancias. Dejando siempre un rastro claro de la actividad que se realiza en cada servicio.

Modelos como **OAuth** u **OpenID** pueden ayudarnos en este cometido.

## Analítica
Es importante conocer el uso que se hace de un API. Saber quién lo consume y de que forma.

Sirve como indicador a los áreas de negocio para saber si un API consigue los valores esperados en la comercialización.

## Escalabilidad
El hecho de exponer los servicios de información a terceros y el abrir la posibilidad de crear nuevas aplicaciones hace que exista la posibilidad de un incremento de llamadas a esos servicios, y por lo tanto incremento de llamadas al backend.

Es por ello que es importante las **arquitecturas de API Management** sean más robustas en cuanto a la escalabilidad se refiere, siendo capaces de aguantar picos grandes de carga.

### Base de Conocimiento
* [5 Rules for API Management][1]
* [API Management. ¿Qué es y para qué sirve?][2]
* [Qué es una API y qué puede hacer por mi negocio][3]

[1]: https://techcrunch.com/2012/11/11/5-rules-for-api-management/
[2]: https://www.paradigmadigital.com/dev/api-management-que-es-y-para-que-sirve/
[3]: https://bbvaopen4u.com/es/actualidad/que-es-una-api-y-que-puede-hacer-por-mi-negocio
