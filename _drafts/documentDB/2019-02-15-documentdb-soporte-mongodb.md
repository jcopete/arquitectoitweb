---
layout: post
title: DocumentDB con soporte MongoDB
excerpt: "¿Qué es DocumentDB?"
categories: documentdb
tags: [nosql, aws, replica set,backup]
image:
  feature: covers/documentdb.jpg
  credit: Samuel Zeller
  creditlink: https://unsplash.com/photos/vpR0oc4X8Mk
comments: true
share: true
author: victor_cuervo
---

Si dentro de tu infraestructura estás gestionando clusters muy grandes de [MongoDB][MongoDB] y se te hace muy complejo o simplemente quieres "olvidarte" de la gestión de dichos clusters, **DocumentDB** puede ser una alternativa. Y es que **DocumentDB** es la [base de datos NoSQL][NoSQL] de Amazon WebServices.

> Existen otras alternativas como podría ser **MongoDB Atlas** que ya trataremos en otro artículo.

Y es que **DocumentDB** es una *base de datos orientada a documentos JSON, completamente gestionada, con alta disponibilidad, escalable y rápida*.

Pero a parte de las características generales que pueden atraernos a utilizar **DocumentDB**, *¿cuál es su principal aliciente?* Este es que **DocumentDB** se comporta igual que **MongoDB**. La idea de **DocumentDB** es poder trabajar con una base de datos [MongoDB][MongoDB] pero optimizada para entornos *"mission critical"* en los cuales tengamos grandes cantidades de escrituras y lecturas.

Para ello **DocumentDB implementa el API Apache 2.0 open source MongoDB 3.6** de tal manera que se puede trabajar como si estuvieses trabajando con una base de datos [MongoDB][MongoDB].

De esta manera se pueden utilizar el mismo código fuente que tengamos, con los mismos drivers que si estuviésemos utilizando la base de datos [MongoDB][MongoDB].

## Capacidades de DocumentDB

* **DocumentDB** es capaz de escalar dede 10Gb a 64TB en incrementos de 10Gb. El almacenamiento está separado del computo, así que se puede incrementar en cualquier momento.

* Las instancias de **DocumentDB** ofrecen diferentes tamaños desde máquinas de 15Gb a máquinas de 488Gb. Se pueden crear hasta 15 réplicas de lectura.

* **DocumentDB** tiene replicados los datos 6 veces en 3 zonas diferentes -AWS Availability Zones (AZs)-. Ante la caida de un un nodo primario es capaz de recuperarse en 30s hacia una de las réplicas. Por lo que la fiabilidad es muy alta.

* El servicio de **DocumentDB** está totalmente gestionado y viene integrado con su monitorización y detección de fallos.

* Se pueden establecer backups dentro de **DocumentDB** de forma diaria mediante *snapshots*. Se puede restaurar puntos de recuperación de hasta 35 días.

* Los datos, réplicas y snapshots que residen en **DocumentDB** pueden ser encriptados mediante la clave que nosotros queramos. De igual manera realiza cifrado "en vuelo" de los datos. Y los servicios de autentificación vienen activados por defecto. Es por ello que está perfectamente preparado para cumplir con la **General Data Protection Regulation (GDPR)**.

## Empezar con DocumenDB

Si quieres empezar a trabajar con **DocumentDB** simplemente [tienes que empezar a configurar paso a paso tu cluster][AWSDocumentDB].

Además, en el caso de que partas de una situación en la que ya tengas un despliegue inicial de [MongoDB][MongoDB], *Amazon WebServices* ofrece un servicio de migración de bases de datos [MongoDB][MongoDB] llamado **AWS Database Migration Service (DMS)** de forma gratuita y por un periodo de 6 meses. Es aplicable a bases de datos que tengamos desplegadas en on-premise o dentro de un *Elastic Compute Cloud (EC2)*.

[MongoDB]: {{site.url}}/mongodb/
[NoSQL]: {{site.url}}/nosql/
[AWSDocumentDB]: https://aws.amazon.com/documentdb/
