---
layout: post
title: Servicios RESTful con Tomcat 7 y Jersey
excerpt: "Apache Derby es un una base de datos relacional (RDBMS) programa completamente en Java y mantenida por la Fundación Apache"
categories: java
tags: [tomcat,restful]
image:
  feature: covers/tomcat.png
comments: true
share: true
author: victor_cuervo
---

Si queremos utilizar JAX-RS para crear nuestros servicios RESTful de una forma sencilla podremos apoyarnos en la implementación que ha hecho Jersey del estándar JAX-RS (JSR 311 y JSR 339). Si bien necesitaremos un servidor para desplegarlos y en este caso vamos a utilizar Tomcat 7 con nuestro ejemplo.

Así que veamos que pasos tenemos que dar para poder crear servicios RESTful con Tomcat 7 y Jersey. En todo el proceso de creación de nuestra aplicación Java con servicios RESTful nos vamos a apoyar en Maven como gestor de dependencias.

# Tomcat 7
Lo primero de todo será utilizar Tomcat 7 para poder disponer de un contenedor de [Servlets][Servlet]. Ya que al final Jersey lo que nos va a proporcionar es un [Servlet][Servlet] el cual deberemos de configurar dentro de nuestro contenedor.

Para utilizar Tomcat 7 vamos a apoyarnos en el plugin de Tomcat para Maven. Así que lo que haremos será configurar el fichero ```pom.xml``` para añadir la referencia a este plugin.

~~~xml
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.tomcat.maven</groupId>
      <artifactId>tomcat7-maven-plugin</artifactId>
      <version>2.2</version>
      <configuration>
        <url>http://localhost:8080/manager/text</url>
        <server>miservidor</server>
        <path>/miapp</path>
      </configuration>
    </plugin>
  </plugins>
</build>
~~~

# Jersey
Para utilizar Jersey necesitamos en primer lugar tener sus librerías, para lo cual lo añadiremos como dependencias Maven y luego configurar el [Servlet][Servlet] que tienen para escuchar las peticiones.

## Añadir dependencia Jersey
Ahora pasamos a añadir la dependencia de Jersey en Maven. Para ello añadimos el siguiente código al fichero ```pom.xml```.

~~~xml
<dependency>
  <groupId>com.sun.jersey</groupId>
  <artifactId>jersey-server</artifactId>
  <version>1.8</version>
</dependency>
~~~

Con esto conseguimos que cuando construyamos nuestro proyecto mediante Maven se gestionen y descarguen las dependencias y sus librerías relacionadas. En este caso: ```jersey-core-1.10.jar```, ```jersey-server-1.10.jar```,...

## Configurar el Servlet Jersey
Una vez tenemos configurado Jersey en nuestro proyecto vamos a dar de alta el [Servlet][Servlet] que atenderá las peticiones para los servicios RESTful. Así que vamos al fichero ```web.xml``` y damos de alta el [Servlet][Servlet].

~~~xml
<servlet>
  <servlet-name>Jersey REST Service</servlet-name>
  <servlet-class>com.sun.jersey.spi.container.servlet.ServletContainer</servlet-class>
  <init-param>
    <param-name>com.sun.jersey.config.property.packages</param-name>
    <param-value>com.lineadecodigo.javaee.rest</param-value>
  </init-param>
  <load-on-startup>1</load-on-startup>
</servlet>
~~~

En la configuración del [Servlet][Servlet] de Jersey vemos varias cosas relevantes. La primera es que el Servlet está en la clase ```com.sun.jersey.spi.container.servlet.ServletContainer``` y el segundo y más importante es que le tenemos que decir cual es la clase base de nuestros servicios RESTful. Para ello utilizamos el parámetro ```com.sun.jersey.config.property.packages``` y en nuestro caso las clases RESTful las tenemos en el paquete ```com.lineadecodigo.javaee.rest```

Lo siguiente será crear un mapping con la ruta en la que queremos que se sirvan los **servicios RESTful**, para ello incluimos en el fichero ```web.xml``` el siguiente código:

~~~xml
<servlet-mapping>
  <servlet-name>Jersey REST Service</servlet-name>
  <url-pattern>/rest/*</url-pattern>
</servlet-mapping>
~~~

# Ejemplo JAX-RS
Ya solo tendremos que crear nuestro servicio RESTful con JAX-RS para poder probarlo. Un ejemplo sencillo de servicio RESTful sería el siguiente Hola Mundo con JAX-RS.

~~~java
package com.lineadecodigo.javaee.rest;

import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.Produces;
import javax.ws.rs.core.Context;
import javax.ws.rs.core.UriInfo;

@Path("helloworld")
public class HelloWorldRest {

  @Context
  private UriInfo context;

  public HelloWorldRest() {}

  @GET
  @Produces("text/html")
  public String getHtml() {
    return "<html lang=\"en\"><body><h1>Hola Mundo!!</h1></body></html>";
  }
}
~~~

# Ejecutar la Aplicación
Como nos hemos basado en Maven para crear servicios RESTful con Tomcat 7 y Jersey deberemos de ejecutar los siguientes comandos para arrancar el servidor.

<kbd>$mvn package clean</kbd>

<kbd>$mvn tomcat7:run-war</kbd>

Ya solo nos quedará acceder a la URL

<samp>http://localhost:8080/miapp/rest/helloworld</samp>

Para ver nuestra aplicación JAX-RS funcionando. Como se puede ver ```miapp``` es el nombre del servidor en Tomcat, ```rest``` es el [Servlet][Servlet] que escucha las peticiones y ```helloworld``` el Path del servicio RESTful.

Si sigues todos estos pasos podrás ya podrás crear tus servicios RESTful con Tomcat 7 y Jersey de una forma sencilla.

[Servlet]: http://lineadecodigo.com/tag/java-servlet/
