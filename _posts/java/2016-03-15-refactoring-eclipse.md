---
layout: post
title: Refactoring en Eclipse
excerpt: "Un refactoring consiste en modificar un código fuente de un programa sin alterar su funcionamiento"
categories: java
tags: [eclipse]
image:
  feature: covers/eclipse.jpg
comments: true
share: true
author: victor_cuervo
---

Un **refactoring** consiste en *modificar un código fuente de un programa sin alterar su funcionamiento*. Esta modificación puede consistir desde una modificación de nombres de elementos ha recodificar partes enteras de código fuente. En este artículo vamos a ver cómo podemos ejecutar un refactoring en Eclipse.

Para ello vamos a partir de un código muy sencillo en el cual tengamos una clase.

~~~java
public class MiClase {  
...
}
~~~

Y lo que queremos es cambiarla de nombre y que así en todos los sitios dónde esté instanciada se cambie al nuevo valor.

Para ello seleccionamos el elemento y pulsamos con el botón derecho. Tendremos un menú que será:

<kbd>Refactor » Rename</kbd>

Nos aparecerá una pequeña ayuda de edición directamente sobre el nombre de la clase.

![Refactoring en Eclipse]({{ site.url }}/images/java/eclipse/refactor.jpg)

Solo tendremos que insertar el nuevo nombre de la clase y pulsar enter. De esta manera todas las referencias que tengamos a esta clase dentro de nuestro código actualizarán automáticamente el nombre de la clase.

Así la próxima vez que tengas que hacer refactoring en Eclipse de tu código fuente no te pasarás un rato realizando buscar y reemplazar.
