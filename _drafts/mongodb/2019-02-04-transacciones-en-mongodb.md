---
layout: post
title: Transacciones en MongoDB 4.0
excerpt: "Análisis del soporte que ofrece MongoDB 4.0 al modelo ACID de transacciones."
categories: mongodb
tags: [nosql,transacciones,mongodb]
image:
  feature: covers/hoja.jpg
comments: true
share: true
author: victor_cuervo
---


Hasta ahora el modelo era "transaccional" a un único documento.
Ahora tiene un modelo de gestión de transacciones ACID multi-documento

ACID ( (Atomicity, Consistency, Isolation, Durability)

Atomicidad, Consistencia, Aislamiento y Durabilidad.

De momento MongoDB 4.0 está como Release Candidate. Disponible en verano 2018

Para ello se basa en los comandos típicos de gestión de transacciones ACID. Lo cuál lo hace muy sencillo de entender para cualquier persona que haya trabajado con una base de datos que gestione transacciones.

	* `start_transaction()`, para iniciar el marco de la transacción.
	* `commit_transaction()`, para confirmar la ejecución de todos los pasos ejecutados en la transacción.
	* `abort_transaction()`, para deshacer los pasos que se hayan ejecutado en el marco de la transacción.


En MongoDB 4.0 la gestión de transacciones funcionará sobre un Replica Set, y a partir de MongoDB 4.2 funcionará con "shared deployment" --> Shared transactions

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
