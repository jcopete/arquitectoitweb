---
layout: post
title: Transacciones en MongoDB 4.0
excerpt: "Análisis del soporte que ofrece MongoDB 4.0 al modelo ACID de transacciones."
categories: mongodb
tags: [nosql,transacciones,mongodb]
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

Hasta la aparición de este modelo transaccional, [MongoDB][MongoDB] trabajaba de forma atómica sobre cada uno de los documentos, ofreciendoles a ellos el modelo transaccional. En esta situación [la forma de modelar las referencias entre documentos para poder asegurar una integridad se realizaban mediante anidación de documentos][AnidacionMongoDB].

Es verdad que existían métodos como [`updateMany`][UpdateMany] que nos permitian actualizaciones a través de múltiples documentos, si bien es verdad que la transaccionalidad se aplicaba de forma atómica en cada uno de los documentos, no en el conjunto de documentos.

El modelo de transaccionalidad de **MongoDB 4.0**, de momento se implementa para un *Replica Set* y [según el roadmap de MongoDB][RoadmapTransacciones] se implementará en **MongoDB 4.2** transacciones para despliegues distribuidos.

## MongoDB implementando Transacciones

En la implementación de transacciones ACID por parte de [MongoDB][MongoDB]

Para ello se basa en los comandos típicos de gestión de transacciones ACID. Lo cuál lo hace muy sencillo de entender para cualquier persona que haya trabajado con una base de datos que gestione transacciones.

	* `start_transaction()`, para iniciar el marco de la transacción.
	* `commit_transaction()`, para confirmar la ejecución de todos los pasos ejecutados en la transacción.
	* `abort_transaction()`, para deshacer los pasos que se hayan ejecutado en el marco de la transacción.


En MongoDB 4.0 la gestión de transacciones funcionará sobre un Replica Set, y a partir de MongoDB 4.2 funcionará con "shared deployment" --> Shared transactions

El inicio es el Replica Set, el futuro transacciones distribuidas


Ya existen modelos anidados en los que se puede gestionar la transaccionalidad de forma atómica en un documento. Y todavía sigue siendo válido.


~~~javascript
with client.start_session() as s:
    s.start_transaction()
    try:
        collection.insert_one(doc1, session=s)
        collection.insert_one(doc2, session=s)
        s.commit_transaction()
    except Exception:
        s.abort_transaction()
~~~



~~~javascript

// v4.0.0-rc0/bin/mongo --port 38000

// ****************************************************
// On a sample person collection with two documents _id 1, 2
// Insert new document, _id 3, inside session1 scope
// Understand how the find operation on these scopes change
// from startTransaction to commitTransaction
// ****************************************************

// drop and recreate person collection with 2 documents _id 1, 2
use test;
db.person.drop();
db.person.insert({"_id": 1, "fname": "fname-1", "lname": "lname-1"});
db.person.insert({"_id": 2, "fname": "fname-2", "lname": "lname-2"});

// create session1 and a collection object using session1 and start a transaction on it
var session1 = db.getMongo().startSession();
var session1PersonColl = session1.getDatabase('test').getCollection('person');
session1.startTransaction({readConcern: {level: 'snapshot'}, writeConcern: {w: 'majority'}});

// insert a document _id 3, inside a transaction/session1
session1PersonColl.insert({"_id": 3, "fname": "fname-3", "lname": "lname-3"});
// WriteResult({ "nInserted" : 1 })

// find the documents from collection and session1
db.person.find()
// { "_id" : 1, "fname" : "fname-1", "lname" : "lname-1" }
// { "_id" : 2, "fname" : "fname-2", "lname" : "lname-2" }

// notice that the insert on session1 is only visible to it.
session1PersonColl.find()
// { "_id" : 1, "fname" : "fname-1", "lname" : "lname-1" }
// { "_id" : 2, "fname" : "fname-2", "lname" : "lname-2" }
// { "_id" : 3, "fname" : "fname-3", "lname" : "lname-3" }

// commit and end the session
session1.commitTransaction()
session1.endSession()

// show the documents after committing the transaction
db.person.find()
// { "_id" : 1, "fname" : "fname-1", "lname" : "lname-1" }
// { "_id" : 2, "fname" : "fname-2", "lname" : "lname-2" }
// { "_id" : 3, "fname" : "fname-3", "lname" : "lname-3" }
~~~


La pregunta es ¿movernos a este modelo de transacciones? o ¿nos mantenemos en el modelo actual?
Es una cuestión de rendimiento.



[NoSQL]: {{site.url}}/nosql/bd-nosql/
[MongoDB]:  {{site.url}}/mongodb/
[AnidacionMongoDB]: http://www.manualweb.net/mongodb/modelado-one-to-one-mongodb/
[UpdateMany]: https://docs.mongodb.com/manual/reference/method/db.collection.updateMany/
[RoadmapTransacciones]: https://www.mongodb.com/blog/post/multi-document-transactions
