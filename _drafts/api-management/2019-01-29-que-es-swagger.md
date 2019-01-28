# ¿Qué es Swagger?

Swagger es una forma estándar de representar un API RESTful. Definir un API RESTful mediante Swagger permite tener una documentación estándar e interactiva del API y generar los SDK para los clientes de una forma muy sencilla.

La versión actual es Swagger 2.0 y es una especificación totalmente OpenSpurce y gestionada por la Open API Initiative.

La idea de Swagger es la de ser agnóstico al lenguaje, pretende que la descripción de un interface sea entendible tanto por un humano como por una máquina, permitiendo entender de una forma rápida las capacidades que ofrece independientemente de la implementación que exista por detrás.

Existen un gran conjunto de herramientas que nos permiten definir un modelo Swagger, verlo de forma visual, generar el cliente para diferentes lenguajes de programación,...

Swagger es una forma estándar de representar un API RESTful. Definir un API RESTful mediante Swagger permite tener una documentación estándar e interactiva del API y generar los SDK para los clientes de una forma muy sencilla.

La versión actual es Swagger 2.0 y es una especificación totalmente OpenSpurce y gestionada por la Open API Initiative.


Dentro de Swagger podemos encontrar herramientas para:
* Swagger UI - https://github.com/swagger-api/swagger-ui
* Swagger Editor - http://editor.swagger.io/
* SDK Generators - https://github.com/swagger-api/swagger-codegen
* Integraciones en el servidor  https://github.com/swagger-api/swagger-codegen
* Servicios - https://github.com/swagger-api/swagger-spec/wiki/Sites-and-Services


La idea de Swagger es la de ser agnóstico al lenguaje, pretende que la descripción de un interface sea entendible tanto por un humano como por una máquina, permitiendo entender de una forma rápida las capacidades que ofrece independientemente de la implementación que exista por detrás.

Existen un gran conjunto de herramientas que nos permiten definir un modelo Swagger, verlo de forma visual, generar el cliente para diferentes lenguajes de programación,...


## Creación de un interface Swagger

Tenemos dos formas de crear un interface Swagger.

### Enfoque API First
Este enfoque se versa en que lo primero que tienes que hacer es crear la descripción del servicio en Swagger, independientemente de cómo vayas a realizar la implementación a posteriori.

En este caso lo primero que necesitaremos será utilizar algún editor de Swagger que nos permita definir el documento swagger basado en la especificación. O bien realizar el diseño de este documento de una forma manual.

Una vez que tengamos nuestro documento Swagger definido podremos utilizar Swagger CodeGen para generar el esqueleto en nuestro lenguaje de servidor preferido. http://swagger.io/getting-started/swagger-codegen


### Enfoque Bottom-Up
La idea es generar el API Swagger desde el código fuente que estemos escribiendo. Existen múltiples librerías que nos permiten añadir anotaciones a nuestro código fuente para que se pueda generar el documento Swagger de forma automática.

## Consumo de un interface Swagger
Cuando vayas a consumir un interface Swagger, te será independiente la estrategia de creación del Swagger que se haya seguido. Ya que en ambos casos el consumir partirá del documento Swagger.

Existe la herramienta Swagger UI, la cual nos permite ver una forma visual el API RESTful definido con Swagger, de igual manera nos permitirá consultar su documentación y navegar por su contenido.

Desde la herramienta Swagger UI podremos generar el cliente en el lenguaje de programaciónq que estemos utilizando, para ello utilizaremos el Swagger Codegen.

## Empezando con Swagger

Desde que los servicios se utilizan como un mecanismo de

Existen diferentes formas de documentar un API REST, la primera aproximación que apareció fue WADL (Web Application Description Language) (http://www.w3.org/Submission/wadl/), una especificación que puede ser entendida por máquinas pero no por humanos la cual se basaba en una definición XML para los elementos del documento. La idea era conseguir lo mismo que se había hecho con los servicios SOA y su WSDL.

WADL fue enviada para ser considerada como especificación por el W3C en agosto de 2009, pero a día de hoy (julio, 2016) sigue sin ser aceptada.

WADL es, hoy por hoy sigue siendo amparado como proyecto de Java.net, https://wadl.java.net/, los cuales han construido generadores de documentos WADL a Java.

Ejemplo de documento WADL.

~~~xml
 1 <?xml version="1.0"?>
 2 <application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 3  xsi:schemaLocation="http://wadl.dev.java.net/2009/02 wadl.xsd"
 4  xmlns:tns="urn:yahoo:yn"
 5  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 6  xmlns:yn="urn:yahoo:yn"
 7  xmlns:ya="urn:yahoo:api"
 8  xmlns="http://wadl.dev.java.net/2009/02">
 9   <grammars>
10     <include
11       href="NewsSearchResponse.xsd"/>
12     <include
13       href="Error.xsd"/>
14   </grammars>
15
16   <resources base="http://api.search.yahoo.com/NewsSearchService/V1/">
17     <resource path="newsSearch">
18       <method name="GET" id="search">
19         <request>
20           <param name="appid" type="xsd:string"
21             style="query" required="true"/>
22           <param name="query" type="xsd:string"
23             style="query" required="true"/>
24           <param name="type" style="query" default="all">
25             <option value="all"/>
26             <option value="any"/>
27             <option value="phrase"/>
28           </param>
29           <param name="results" style="query" type="xsd:int" default="10"/>
30           <param name="start" style="query" type="xsd:int" default="1"/>
31           <param name="sort" style="query" default="rank">
32             <option value="rank"/>
33             <option value="date"/>
34           </param>
35           <param name="language" style="query" type="xsd:string"/>
36         </request>
37         <response status="200">
38           <representation mediaType="application/xml"
39             element="yn:ResultSet"/>
40         </response>
41         <response status="400">
42           <representation mediaType="application/xml"
43             element="ya:Error"/>
44         </response>
45       </method>
46     </resource>
47   </resources>
48
49 </application>
~~~

Otras alternativas, más realistas:

* RAML
* API Blueprint


## Pero, ¿qué es Swagger?
Swagger es un conjunto de reglas para poder definir un API REST, no tiene por qué ser necesariamente RESTful.

El formato de Swagger 2.0 puede ser bien JSON o bien YAML.

Un ejemplo de documento Swagger sería

~~~yaml
swagger: "2.0"
info:
  version: "1.0"
  title: "Hello World API"
paths:
  /hello/{user}:
    get:
      description: Returns a greeting to the user!
      parameters:
        - name: user
          in: path
          type: string
          required: true
          description: The name of the user to greet.
      responses:
        200:
          description: Returns the greeting.
          schema:
            type: string
        400:
          description: Invalid characters in "user" were provided.
~~~

En este ejemplo podemos ver el API Hello World, el cual define una única URL de consumo "/hello/{user}", dicha URL acepta como parámetro el nombre del uusario al cual se saludará como respuesta de invocación de la URL.

La especificación Swagger nos enseña a como definir:

* Paths
* Parémtros
* Respuestas
* Modelos
* Seguridad
* y más

## Estructura de un fichero Swagger
La definición Swagger debe de estar en un único fichero, si bien, partes de la definición pueden extraerse a otros ficheros. La externalización es apicable a los campos $ref, atendiendo a la especificación del JSON Schema.

La definición swagger se guardará en un fichero swagger.json


## Tipos de Datos
Los tipos de datos soportados por la especificación Swagger son los definidos en el [JSON Schema Draft 4][4]. Los modelos están descritos utilizando el [Schema Object][4] que es un subconjunto del [JSON Schema Draft 4][4].

Un tipo de dato primitivo adicional es file, el cual es utilizado por el objeto Response y el objeto Parameter para indicar que en la respuesta o bien como parámetro de petición tenemos un fichero.

Los tipos de datos que podemos tener son:

|Nobre Común|Tipo|Formato|Comentario|
|---|---|---|---|
|integer|integer|int32|signed 32 bits|
|long|integer|int64|signed 64 bits|
|float|number|float||
|double|number|double||
|string|string|||
|byte|string|byte|base64 encoded characters|
|binary|string|binary|any sequence of octets|
|boolean|boolean|||
|date|string|date|As defined by full-date - RFC3339|
|dateTime|string|date-time|As defined by date-time - RFC3339|
|password|string|password|Used to hint UIs the input needs to be obscured.|


Los tipos adicionalmente tienen un formato, para el caso de las cadenas podemos encontrarnos con diferentes valores para el formato, ya que es un valor abierto. Así nos podemos encontrar con "email", "uuid"

## Objeto Swagger
Es el objeto raíz del documento y de la especificación. Mediante el objeto Swagger podremos definir la declaración del API

* swagger:string, indica la versión de la especificación de Swagger que estamos utilizando, por ejemplo la "2.0".
* info:ObjetoInfo (obligatorio), nos permite definir la metadata del API.
* host:string, el nombre o IP del host que sirve el API. Solo debe de ser el nombre del host y su puerto. No debe de incluir paths. En el caso de que no se especifique el host se utilizará el mismo host que sirva la documentación.
* basePath:string, el path en el que el API es servido, este path es relativo al host. El path debe de empezar por "/".
* schemes:[string], protocolos por el cual atenderá el API. Los valores serán: "http", "https", "ws", "wss". En el caso de no especificar valor en schemes se utilizará el que se haya utilizado para acceder a la documentación.
* consumes:[string], una lista de todos los mime-types que puede consumir el API.
* produces[string], una lista de todos los mime-types que puede producir el API.
* paths:ObjetoPath (obligatorio), este objeto especifica todos los paths y operaciones que contiene en API.
* definitions:DefinitionsObject, es un objeto que contiene todos los tipos de datos que pueden ser consumidos o producidos por las operaciones del API.
* parameters:ParametersDefinitionsObject, objeto que contiene la definición de los parámetros que pueden ser utilizados por las operaciones del API.
* responses:ResponseDefinitionsObject, objeto que contiene todas las respuestas que pueden ser utilizadas por las operaciones del API.
* securityDefinitions:SecurityDefinitionsObject, definiciones del schema de seguridad que puede ser utilizado en la especificación.
* security:[SecurityRequirementObject], lista de qué esquemas de seguridad pueden ser aplicados para el API "como un todo". Las operaciones individuales pueden sobrescribir este valor.
* tags:[TagObject], lista de tags utilizadas como metada del API. No todas las tags utilizadas por el OperationObject deben de ser declaradas. Las tags deben de tener identificadores únicos.
* externalDocs:ExternalDocumentationObject, documentación adicional externa.

El objeto Swagger puede ser ampliado por extensiones del vendedor, la cuales empezarán por x-, por ejemplo x-internal-id.

Así la estructura de nuestro objeto Swagger podría ser la siguiente:

## Objeto Info
Es el objeto que nos permite especificar el metadata del API. Los campos que podemos meter en el objeto info son:

* title:string (obligatorio), es el título del API.
* description:string, es la descripción del API. Se soporta la sintaxis GFM para mostrar contenido rico de la descripción.
* termsOfService:string, términos de servicio del API.
* contact:ContactObject, información sobre el contacto del API.
* license:LicenseObject, información sobre la licencia del API.
* version:string (obligatorio), indica la versión del API.

Un ejemplo, en formato JSON, sería:

{
  "title": "Cuanto Sabes De",
  "description": "Este es un API para poder crear test.",
  "termsOfService": "http://www.cuantosabesde.com/terms/",
  "contact": {
    "name": "Cuanto Sabes De",
    "url": "http://www.cuantosabesde.com/contacto",
    "email": "api@cuantosabesde.com"
  },
  "license": {
    "name": "Apache 2.0",
    "url": "http://www.apache.org/licenses/LICENSE-2.0.html"
  },
  "version": "1.0"
}
 Y en formato YAML:

{{ Ponerlo }}

## Objeto Contacto
Sirve para describir cual es el contacto para el API. Los campos que podemos describir son:

* name:string, nombre de la persona u organización de contacto.
* url:string, una URL dónde se pueden poner en contacto. Debe de ser una URL.
* email:string, email del contacto, persona u organización. Debe de ser un email.

"contact": {
    "name": "Cuanto Sabes De",
    "url": "http://www.cuantosabesde.com/contacto",
    "email": "api@cuantosabesde.com"
  }


## Objeto Licencia
Información sobre la licencia asociada al API. Los campos que podemos describir son:

* name:string, nombre de la licencia utilizada por el API.
* url:string, url que contiene la licencia utilizada por el API.

"license": {
    "name": "Apache 2.0",
    "url": "http://www.apache.org/licenses/LICENSE-2.0.html"
  }


## URLs de Apoyo

* [Especificación Swagger][1]
* [What's Swagger][2]
* [Swagger Getting Startted][3]

[1]: http://swagger.io/specification/
[2]: http://swagger.io/getting-started-with-swagger-i-what-is-swagger/
[3]: http://swagger.io/getting-started/
[4]: http://json-schema.org/latest/json-schema-core.html#anchor8 "JSON Schema Draft 4"
