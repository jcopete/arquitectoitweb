---
layout: post
title: Límite de subida de ficheros en Nginx
excerpt: "El límite por defecto de subida de ficheros en Nginx es de 1Mb, veamos como podemos aumentar y controlar dicho límite."
categories: nginx
tags: [nginx,servidores,configuracion]
image:
  feature: covers/nginx.png
comments: true
share: true
author: victor_cuervo
---

Por defecto cuando instalamos un servidor **Nginx** este viene con un límite de subida de ficheros de 1Mb. Y si estamos haciendo una web con **Ngix** e intentamos subir ficheros de mayor tamaño nos podemos volver locos.

Si queremos aumentar el límite de subida en los ficheros con **Nginx** deberemos de utilizar la directiva `client_max_body_size`, que es parte del móduo **ngx_http_core_module**.

La directiva `client_max_body_size` debe de establecerse en el contexto **server**, **http** o **location**.

Lo que tenemos que hacer es poner la directiva en el fichero de configuración de **Ngix** `/etc/nginx/nginx.conf`.

Si lo queremos hacer a nivel de servidor para que se aplique a todas las aplicaciones registradas lo haremos a nivel de **http**

~~~conf
http {
    ...
    client_max_body_size 50M;
}  
~~~

> En este caso hemos aumentado la posibilidad de subir ficheros al servidor **Nginx** de hasta 50Mb.

Si queremos que sea para un sitio en concreto de los registrados lo haremos a nivel de **server**:

~~~conf
server {
    ...
    client_max_body_size 50M;
}  
~~~

Y si queremos que sea para una ruta en específico lo hacemos a nivel de **location**:

~~~conf
location /upload {
    ...
    client_max_body_size 50M;
}  
~~~

Una vez que hayamos configurado el servidor **Ngix** deberemos de comprobar que la sintaxis de su fichero es correcta. Para ello ejecutamos en la consola:

~~~sh
$ sudo nginx -t
~~~

Finalmente deberemos de reiniciar el servidores

~~~sh
$ sudo systemctl restart nginx
~~~

Si intentamos hacer una petición mayor del tamño establecido por configuración, el servidor nos devolverá un **413 (Request Entity Too Large)**.

**Es importante controlar el tamaño de los ficheros que nos pueden subir al servidor y de las rutas desde las cuales se pueden subir**. Ya que subir ficheros de un gran tamaño puede hacer que nuestro servidor sea más susceptible a ser vulnerable en temas de seguridad.
