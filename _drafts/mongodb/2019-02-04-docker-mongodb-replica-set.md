---
layout: post
title: Docker MongoDB con Replica Set
excerpt: "Qué es un Replica Set"
categories: mongodb
tags: [nosql,transacciones,mongodb]
image:
  feature: covers/hoja.jpg
comments: true
share: true
author: victor_cuervo
---


docker container run --detach --publish 27017:27017 --name mongo mongo --replSet rs0


[NoSQL]: {{site.url}}/nosql/bd-nosql/
[MongoDB]:  {{site.url}}/mongodb/
