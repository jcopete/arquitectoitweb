---
layout: post
title: Transacciones en MongoDB 4.0
excerpt: "Análisis del soporte que ofrece MongoDB 4.0 al modelo ACID de transacciones sobre multi-documentos."
categories: mongodb
tags: [transacciones,acid,sesiones]
image:
  feature: covers/hoja.jpg
  credit: Martin Castro
  creditlink: https://unsplash.com/photos/dlMui5b3yR4
comments: true
share: true
author: victor_cuervo
---

Para los más puristas de los [modelos NoSQL][NoSQL] y sobre todo de los usuarios de la base de datos [NoSQL][NoSQL] basada en documentos [MongoDB][MongoDB] el hecho de disponer de transacciones en el motor de MongoDB podía suponer un verdadero ultraje a los principios del modelo.

Si bien es verdad que diferentes escenarios, principalmente en entornos financieros, llevaron a que en la versión **MongoDB 4.0** se implentase un *modelo transaccional ACID (Atomicidad, Consistencia, Aislamiento y Durabilidad.)* sobre diferentes documentos.

Hasta la aparición de este modelo transaccional, [MongoDB][MongoDB] trabajaba de forma atómica sobre cada uno de los documentos, ofreciendoles a ellos el modelo transaccional. En esta situación [la forma de modelar las referencias entre documentos para poder asegurar una integridad se realizaban mediante anidación de documentos][AnidacionMongoDB]. Este modelo para la gestión de transacciones sigue siendo válido, aunque dispongamos del nuevo mecanismo ACID.

Es verdad que existían métodos como [`updateMany`][UpdateMany] que nos permitian actualizaciones a través de múltiples documentos, si bien es verdad que la transaccionalidad se aplicaba de forma atómica en cada uno de los documentos, no en el conjunto de documentos.

El modelo de transaccionalidad de **MongoDB 4.0**, de momento se implementa para un *Replica Set* y [según el roadmap de MongoDB][RoadmapTransacciones] se implementará en **MongoDB 4.2** transacciones para despliegues distribuidos.

## Métodos Transacciones MongoDB

Lo primero que tenemos que hacer para utilizar las transacciones en [MongoDB][MongoDB] es conocer los métodos que nos ofrecen.

Por un lado tenemos métodos para gestionar la sesión:

* `startSession()`, las transacciones están asociadas a una sesión, es por ello que siempre necesitaremos abrir una sesión.
* `endSession()`, cuando cerremos la sesión, si hay alguna transacción ejecutándose, esta se abortará.

Y por otro los métodos para controlar la transacción:

* `Session.startTransaction()`, este método nos sirve para empezar la transacción multi-documento dentro de una sesión.
* `Session.commitTransaction()`, con este método confirmaremos los cambios que hayamos realizado dentro de la transacción.
* `Session.abortTransaction()`, aborta la ejecución de la transacción y por lo tanto no graba las modificaciones hechas a lo largo de la transacción.

## Ejemplo MongoDB Transacción
Ahora vamos a ejecutar paso a paso una transacción desde el *shell* de [MongoDB][MongoDB] para ver cómo funcionan las transacciones en [MongoDB][MongoDB]

> Es importante que tengas [MongoDB][MongoDB] arrancado en **formato Replica Set**. Ya que si lo tienes en modo standalone no te funcionará las transacciones en [MongoDB][MongoDB].

Lo primero será crear una base de datos con algo de contenido:

~~~javascript
use test;
db.personas.drop();
db.personas.insert({"_id": 1, "nombre": "Ignacio", "apellido": "Santos"});
db.personas.insert({"_id": 2, "nombre": "Rodrigo", "apellido": "Muñoz"});
~~~

Ahora crearemos la sesión y de la sesión elegimos la colección sobre la que vamos a actuar:

~~~javascript
var sesion = db.getMongo().startSession();
var personas = sesion.getDatabase('test').getCollection('personas');
~~~

Lo siguiente será crear la transacción mediante el método `startTransaction()`:

~~~javascript
sesion.startTransaction({readConcern: {level: 'snapshot'}, writeConcern: {w: 'majority'}});
~~~

Y acto seguido insertaremos un documento:

~~~javascript
personas.insert({"_id": 3, "nombre": "Javier", "apellido": "García"});
~~~

Al estar sin confirmar la transacción, si hacemos una consulta sobre la base de datos de personas veremos lo siguiente:

~~~javascript
db.personas.find()
{ "_id" : 1, "nombre" : "Ignacio", "apellido" : "Santos" }
{ "_id" : 2, "nombre" : "Rodrigo", "apellido" : "Muñoz" }
~~~

Es decir, el documento todavía no se encuentra insertado en la colección. Pero sí en el ámbito de la transacción

~~~javascript
personas.find()
{ "_id" : 1, "nombre" : "Ignacio", "apellido" : "Santos" }
{ "_id" : 2, "nombre" : "Rodrigo", "apellido" : "Muñoz" }
{ "_id" : 3, "nombre" : "Javier", "apellido" : "García" }
~~~

Ahora lo que haremos será confirma la transacción mediante `commitTransaction()` y cerrar la sesión:

~~~javascript
sesion.commitTransaction()
sesion.endSession()
~~~

Ya podremos comprobar que el documento insertado mediante la transacción se encuentra en la colección:

~~~javascript
db.personas.find()
{ "_id" : 1, "nombre" : "Ignacio", "apellido" : "Santos" }
{ "_id" : 2, "nombre" : "Rodrigo", "apellido" : "Muñoz" }
{ "_id" : 3, "nombre" : "Javier", "apellido" : "García" }
~~~

Si hubiésemos utilizado el método `abortTransaction()` no se habría visto reflejado.

El código completo sería:

~~~javascript
use test;
db.personas.drop();
db.personas.insert({"_id": 1, "nombre": "Ignacio", "apellido": "Santos"});
db.personas.insert({"_id": 2, "nombre": "Rodrigo", "apellido": "Muñoz"});
var sesion = db.getMongo().startSession();
var personas = sesion.getDatabase('test').getCollection('personas');
sesion.startTransaction({readConcern: {level: 'snapshot'}, writeConcern: {w: 'majority'}});
personas.insert({"_id": 3, "nombre": "Javier", "apellido": "García"});
db.personas.find()
// { "_id" : 1, "nombre" : "Ignacio", "apellido" : "Santos" }
// { "_id" : 2, "nombre" : "Rodrigo", "apellido" : "Muñoz" }
personas.find()
// { "_id" : 1, "nombre" : "Ignacio", "apellido" : "Santos" }
// { "_id" : 2, "nombre" : "Rodrigo", "apellido" : "Muñoz" }
// { "_id" : 3, "nombre" : "Javier", "apellido" : "García" }
sesion.commitTransaction()
sesion.endSession()
db.personas.find()
// { "_id" : 1, "nombre" : "Ignacio", "apellido" : "Santos" }
// { "_id" : 2, "nombre" : "Rodrigo", "apellido" : "Muñoz" }
// { "_id" : 3, "nombre" : "Javier", "apellido" : "García" }
~~~

## Conclusiones sobre Transacciones MongoDB

Ya hemos visto que puede ser muy útil el uso de transacciones en [MongoDB][MongoDB]. Si bien debemos tener claro el peaje a pagar. El modelo de documentos anidados sigue siendo muy válido para algunos escenarios.

Así, la pregunta sería ¿tenemos que movernos a este modelo de transacciones? o ¿nos mantenemos en el modelo actual? Cuestión de rendimiento.


[NoSQL]: {{site.url}}/nosql/bd-nosql/
[MongoDB]:  {{site.url}}/mongodb/
[AnidacionMongoDB]: http://www.manualweb.net/mongodb/modelado-one-to-one-mongodb/
[UpdateMany]: https://docs.mongodb.com/manual/reference/method/db.collection.updateMany/
[RoadmapTransacciones]: https://www.mongodb.com/blog/post/multi-document-transactions
