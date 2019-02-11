---
layout: post
title: ¿Qué es DocumentDB?
excerpt: "¿Qué es DocumentDB?"
categories: documentdb
tags: [nosql, aws]
image:
  feature: covers/hoja.jpg
comments: true
share: true
author: victor_cuervo
---


## Qué es DocumentDB

AWS DocumentDB es una base de datos documental completamente gestionada, con alta disponibilidad, escalable y rápida.


## DocumentDB compatible con MongoDB

https://aws.amazon.com/documentdb/


Existe una complicación a la hora de gestionar un cluster [MongoDB][MongoDB]
La idea de DocumentDB es poder trabajar con una base de datos [MongoDB][MongoDB] pero optimizada para entornos *"mission critical"* en los cuales tengamos grandes cantidades de escrituras y lecturas.

Para ello DocumentDB implementa el API **Apache 2.0 open source MongoDB 3.6** de tal manera que se puede trabajar como si estuvieses trabajando con una base de datos [MongoDB][MongoDB].

De esta manera se pueden utilizar los mismos drivers que si estuviésemos utilizando la base de datos [MongoDB][MongoDB]

DocumentDB es capaz de escalar más de 64TB por cada base de datos del cluster.

DocumentDB separa el computo del almacenamiento lo que le permite escalar las réplicas de una forma ágil en el caso de que necesitemos ampliar las capacidades de lectura.

DocumentDB tiene replicados los datos 6 veces en 3 zonas diferentes -AWS Availability Zones (AZs)-


Se ofrece un servicio de migración de bases de datos [MongoDB][MongoDB] llamado AWS Database Migration Service (DMS) de forma gratuita y por un periodo de 6 meses. Es aplicable a bases de datos que tengamos desplegadas en on-premise o dentro de un Elastic Compute Cloud (EC2)


## Configurar el Cluster

(Seguir documento para la prueba del cluster)
(Cómo movernos por los clusters)

https://aws.amazon.com/blogs/aws/new-amazon-documentdb-with-mongodb-compatibility-fast-scalable-and-highly-available/


[MongoDB]:{{site.url}}/mongodb
