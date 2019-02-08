---
layout: post
title: Contenedores IBM
excerpt: "bla bla bla"
categories: cloud
tags: [serverless]
image:
  feature: covers/dialogflow.jpg
comments: true
share: true
author: victor_cuervo
---


## Qué es un contenedor
* Un grupo de procesos que se ejecutan de forma aislada
* Cada contenedor tiene su conjunto de **namespaces**. Los **namespaces** que offece un contenedor de forma aislada son:


  * pid - procesos
  * user - usuarios y grupos
  * uts - hostname y domainname
  * ns - mont points
  * net - dispositivos de red, puertos,...
  * ipc - comunicaciones entre procesos



  MNT: Mount and unmount directories without affecting other namespaces.
  NET: Containers have their own network stack.
  IPC: Isolated interprocess communication mechanisms such as message queues.
  User: Isolated view of users on the system.
  UTC: Set hostname and domain name per container.



 * **mnt**, para montar y desmontar directorios.
 * **net**, el contenedor dispone de su propio stack de red.
 * **ipc**, mecanismos de comunicación entre procesos, por ejemplo colas de mensajes.
 * **user**, su propia vista de usuarios y grupos de usuarios del sistema.
 * **utc**, para tener un hostname y domain por contenedor.

 Al tener aislamiento en estos namespaces hace que se pueda estar ejecutando varios cotenedores en el mismo sistema.


Los contneedores ofrecen namesapces y control groups:

* cgroups (control groups), control de grupos y monitorización

* Los contenedores llevan en linux más de 10 años, con lo cual no es una tecnología moderna.

## VM versus contenedores
* Cada VM tiene su propio SO y es muy pesada
* Contenedores no tienen un SO, si no que solo un conjunto específico de contenedores. Los contenedores comparten el mismo kernel.

* El aislamiento de los procesos del contenedor es proporcionado por los Linux Namespaces. Esto hace que su arranque sea muy rápido. Más rápido que las máquinas virtuales.

* Contenedores no sustituten a las VM. Si no que se complementan, incluso pueden ejecutarse sobre la VM.

## Qué es un Docker

Las utilidades que exitian para gestionar contenedores eran complejas. Es por ello que aparece Docker.

Docker crea un conjunto de tools para que se pueda extender el uso de contenedores.

Permite a los desarrolladores y operadores empaquetar aplicaciones dentro de los contenedores. E integrar esta integración en los pipelines CI/CD.

Esto nos permite ir a un modelo de único despliegue de las aplicaciones. Lo cual reduce los tiempos de configuración de los entornos.

Las aplicaciones se empaquetan con todas las funcionalidades que necesitan para ser ejecutadas. De esta manera cuando ejecutemos el contenedor en otro entorno nos vamos a asegurar que se ejecuta de la misma manera.

Las modificaciones sobre el entorno se hacen directamente sobre la imagen.

Los contenedores aprovechan los recursos mejor que una VM, ya que se pueden ajutar más contenedores que VM a una máquina física.

Los contenedores ofrecen un interface estandar a los desarrolladores. Ya que les puedes ofrecer una imagen con lo que ellos necesiten y simplemente utilizand un `docker run`.

Docker ofrece un conjunto de herramientas, desarrolladas por la comunidad en proyectos opensource, que resuelven problemas comunes como puede ser la "orquestación de contenedores".


## Ejecutar un contenedor

`$ docker container run -t ubuntu top`
Ejecuta el comando top para sacar los procesos. Al no tener la imagen ubuntu la descarga

`$ docker container ls`
Lista los contenedores disponibles

~~~sh
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
84d711ce23e0        ubuntu              "top"               32 seconds ago      Up 31 seconds                           optimistic_hodgkin
fc6aa677306c        ubuntu              "top"               9 minutes ago       Up 9 minutes                            agitated_tereshkova
~~~

`$ docker container exec -it b3ad2a23fab3 bash`
Mediante la opción exec y bash podemos inspeccionar el contenido del contenedor.


Docker se basa en **Linux Kit** que es un proyecto opensource que nos permite ejecutar contenedores en diferentes plataformas (Windows/Mac) ofreciendo un subsistema Linux.

De esta manera Docker nos permite ofrecer la capacidad de los contenedores a muchas plataformas y así extenderse más.
