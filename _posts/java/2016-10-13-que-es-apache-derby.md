---
layout: post
title: ¿Qué es Apache Derby?
excerpt: "Apache Derby es un una base de datos relacional (RDBMS) programa completamente en Java y mantenida por la Fundación Apache"
categories: java
tags: [apache,databases]
image:
  feature: covers/databases.png
comments: true
share: true
author: victor_cuervo
---

Apache Derby es un una base de datos relacional (RDBMS) programa completamente en Java y mantenida por la Fundación Apache. El proyecto Apache Derby es un proyecto OpenSource bajo licencia Apache 2.0.

> Oracle distribuye el proyecto Apache Derby como Java DB.

Una de las principales características es que Apache Derby puede ser incrustado dentro de nuestros programas Java, ocupando solo 2,6Mb de espacio, y funcionando directamente en memoria.

# Historia
Apache Derby fue desarrollado en primer momento por Cloudscape allá por 1997. Tras múltiples compras Cloudscape acabaría siendo comprada por IBM quien renombró a la base de datos como IBM Cloudscape.

En 2004 IBM cede el código a la Fundación Apache para el proyecto Derby, el cual era originariamente Java DB.

# Características
Dentro de las características de Apache Derby encontramos:

* Está escrita completamente en Java.
* Se basa en los estándares SQL y JDBC.
* Proporciona un driver JDBC que puede ser incrustado directamente en nuestra aplicación Java.
* Ocupa solo 2,6Mb
* Soporta un funcionamiento cliente/servidor.
* Puede ser ejecutada directamente en memoria.
* Soporta múltiples Schema
* Tiene capacidad de ejecutar procedimientos almacenados
* Tiene soporte multi-idioma vía localización.

# Modos de despliegue
Apache Derby puede ser desplegada de dos formas:

## Incrustada
Es ejecutada como una aplicación Java. En este caso la base de datos corre en la misma Java Virtual Machine (JVM) que la aplicación. El arranque de la aplicación se hace en el mismo momento que arranca la aplicación.

En este caso estamos ejecutando los datos en memoria.

## Servidor
Es el modo tradicional de las bases de datos. En este caso permite que se puedan conectar a ella múltiples usuarios. La base de datos se ejecutará en una Java Virtual Machine (JVM) que estará desplegada en un servidor.

Se conoce como Derby Network Server. Y funciona en una configuración cliente/servidor.

# Conectar Apache Derby con JDBC
Aquí tenemos un pequeño código que nos permite conectar nuestra base de datos con el programa Java. Ejecutándolos juntos en memoria.

~~~java
Connection con = null;

String sURL = "jdbc:derby:memory:myDB;create=true";

try {

  con = DriverManager.getConnection(sURL);	      	      

  // Creamos la tabla
  PreparedStatement tabla = con.prepareStatement("CREATE TABLE country (country varchar(100) not null)");
  tabla.execute();

  // Insertamos datos	      
  Statement carga = con.createStatement();
  carga.addBatch("INSERT INTO country VALUES ('Spain')");
  carga.addBatch("INSERT INTO country VALUES ('France')");
  carga.addBatch("INSERT INTO country VALUES ('United States')");
  carga.addBatch("INSERT INTO country VALUES ('Brazil')");
  carga.addBatch("INSERT INTO country VALUES ('Japan')");	     
  carga.executeBatch();

} catch (Exception e) {
  System.out.println("Error en la conexión:" + e.toString() );
}
~~~

# Descargar Apache Derby
Puedes descargarte la base de datos Apache Derby desde http://db.apache.org/derby/derby_downloads.html.

En el caso de que estés utilizando un gestor de dependencias como Maven y quieras utilizarla directamente en memoria puedes añadir la siguiente dependencia.

~~~xml
<dependency>
  <groupId>org.apache.derby</groupId>
  <artifactId>derby</artifactId>
  <version>10.12.1.1</version>
  <scope>compile</scope>
</dependency>
~~~
