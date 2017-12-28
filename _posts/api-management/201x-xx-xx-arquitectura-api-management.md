# Arquitectura API Management

Aunque cada producto que encontramos en el mercado tiene una **arquitectura API Management** diferente, podríamos identificar, de manera conceptual, que al menos deberían de existir tres piezas:

* API Portal
* API Gateway
* API Manager

Luego, dependiendo del producto que escojamos dentro de nuestra estrategia de **API Management** podremos encontrarnos que alguna no está, o está incluida en otra, o añaden nuevas piezas. Pero esto lo iremos viendo cuando revisemos las arquitecturas de los productos de **API Management**.

---


* Gateway
* Developer Portal
  * Es el portal dónde los desarrolladores se pueden registrar a las APIs. La idea es eliminar la dependencia de una persona en el onboarding
* Analytics Portal
* API Service Development UI ¿Manager?
  * Dónde se despliegan y gestionan las APIs


1. Dónde atacan las aplicaciones -> Gateway
2. Dónde se suscriben las apps -> Manager??






## API Portal

## API Gateway

## API Manager


Todo API Management debe de permitir:
* Composición y orquestación
    * Conseguir que los servicios de backend sean expuestos como APIs
* Seguridad
    * Proteger los activos expuestos contra ataques de seguridad
* Identidad
    * Permitir que los clientes tengan un acceso seguro y que sea transparente para las aplicaciones de backend.
* Rendimiento y Ciclo de Vida
    * Asegurar la disponibilidad de los APIs para las aplicaciones cliente.
* Gestión de Desarrolladores
    * Permitir un onboarding, educación y gestión de los desarrolladores.


<img src="images/arquitectura-api.png" alt="API Gateway" class="img-responsive"/>

*Gráfico definido por [API Academy][1]*

## API Gateway

El componente core de un API Management es el API Gateway.
Es un componente de red que interactua como proxy contra las aplicaciones cliente
El API Gateway puede ser virtual o físico
El API Gateway es el punto central dónde toda la funcionalidad es alojada y gestionada atendiendo a un conjunto de políticas de gobierno.

Características:
* Seguridad
* Caché
* Orquestación
* Representación del API

Capacidades del API Gateway:
* Seguridad, proteger los backends ante ataques de seguridad externos.
* Rendimiento,proporcionar el mejor tiempo respuesta ante las peticiones de los clientes.
* Transformación de Datos, convertir los datos de los backends en datos que sean user-friendly para la capa de APIs.
* Orquestación, componer nuevos APIs mediante la composición de varios backends.
* Logging, grabación de mensajes de las peticiones para poder hacer analítica y auditoría.

El Gateway nos proporcionará una abstracción de la gestión de claves en el API, evitando que esta gestión se tenga que hacer en los backends.

El hecho de que el API Gateway esté centralizado nos sirve como un punto consistente para la aplicación de políticas de gobierno.

<img src="images/api-gateway.png" alt="API Gateway" class="img-responsive"/>

## API Portal

La idea es que el API sea user-friendly para los desarrolladores. Es por ello que la funcionalidad de los APIs es expuesta en un portal.
Normalmente se añade un portal web en el Gateway.
Será el portal dónde los desarrolladores se registren, puedan acceder a la documentación del portal y a la información de rendimiento y consumo de las APIs.

Características
* Documentación
* Proceso de registro de desarrolladores
* Análisis de estadísticas
* Comunidad

El API Portal está dirigido a los desarrolladores, mediante el API Portal facilitaremos el proceso de enrollment. Pasando a ofrecerles toda la documentación disponible, así como el acceso a los recursos, buenas prácticas,…

Las funcionalidades que un API Portal debe de tener son:

* Descubrimiento, hacer simple a los desarrolladores encontrar y aprender sobre APIs.
* Onboarding, permitir a los desarrolladores suscribirse a los diferentes planes para poder utilizar los APIs.
* Educación, proporcionar información a los desarrolladores sobre cómo manipular los APIs.
* Ejemplos, ilustrar el uso de los APIs ofreciendo partes de código que utilicen las funcionalidades
* Comunidad, proporcionar a los desarrolladores la capacidad de compartir buenas prácticas entre ellos.
* Analítica, información sobre el uso y rendimiento del API.

<img src="images/api-portal.png" alt="API Portal" class="img-responsive"/>


[1]: http://www.apiacademy.co/resources/api-management-101-api-management-basics/
