[Drive de la materia (Material)](https://drive.google.com/drive/u/1/folders/1IzoSBcLlCac7pMZcgjdvKrKyLSdobenA)

![[guia-practica-r0.pdf]]

# Indice

- [[#1|1]]
	- [[#1#E1.|E1.]]
	- [[#1#E2.|E2.]]
	- [[#1#E3.|E3.]]
	- [[#1#E4.|E4.]]
		- [[#E4.#Unicode|Unicode]]
		- [[#E4.#UTF-8|UTF-8]]
	- [[#1#E5.|E5.]]
	- [[#1#E6.|E6.]]
	- [[#1#E7.|E7.]]
	- [[#1#E8.|E8.]]
		- [[#E8.#Little Endian|Little Endian]]
		- [[#E8.#Big Endian|Big Endian]]
	- [[#1#E9.|E9.]]
		- [[#E9.#Archivos de Texto Plano|Archivos de Texto Plano]]
		- [[#E9.#Archivos Binarios|Archivos Binarios]]
	- [[#1#E10.|E10.]]
		- [[#E10.#Métodos de Serialización (como está la info)|Métodos de Serialización (como está la info)]]
		- [[#E10.#Null terminated vs chunked|Null terminated vs chunked]]
			- [[#Null terminated vs chunked#**Codificación Null-terminated**|**Codificación Null-terminated**]]
			- [[#Null terminated vs chunked#**Codificación chunked (por bloques)**|**Codificación chunked (por bloques)**]]
	- [[#1#12|12]]
	- [[#1#13|13]]
	- [[#1#14|14]]
	- [[#1#15|15]]
	- [[#1#16|16]]
	- [[#1#17|17]]
	- [[#1#18|18]]
	- [[#1#19|19]]
		- [[#19#a|a]]
		- [[#19#b, c|b, c]]
	- [[#1#20|20]]
		- [[#20#A|A]]
		- [[#20#B|B]]
	- [[#1#21|21]]
	- [[#1#22|22]]
- [[#HTTP: Funcionalidades que provee el protocolo|HTTP: Funcionalidades que provee el protocolo]]
	- [[#HTTP: Funcionalidades que provee el protocolo#23|23]]
	- [[#HTTP: Funcionalidades que provee el protocolo#24|24]]
	- [[#HTTP: Funcionalidades que provee el protocolo#25|25]]
		- [[#25#¿Qué es un media type?|¿Qué es un media type?]]
	- [[#HTTP: Funcionalidades que provee el protocolo#26|26]]
		- [[#26#A|A]]
		- [[#26#B|B]]
		- [[#26#Pipelining|Pipelining]]
	- [[#HTTP: Funcionalidades que provee el protocolo#27|27]]
	- [[#HTTP: Funcionalidades que provee el protocolo#28|28]]
	- [[#HTTP: Funcionalidades que provee el protocolo#29|29]]
		- [[#29#302 Found|302 Found]]
		- [[#29#403  Forbidden|403  Forbidden]]
		- [[#29#405 Not allowed|405 Not allowed]]
		- [[#29#401 Unauthorized|401 Unauthorized]]
		- [[#29#409 Conflict|409 Conflict]]
		- [[#29#410 Gone|410 Gone]]
		- [[#29#404 Not Found|404 Not Found]]
		- [[#29#400 Bad request|400 Bad request]]
		- [[#29#415 Unsuported Media Type|415 Unsuported Media Type]]
		- [[#29#503 Service Unavailable|503 Service Unavailable]]
	- [[#HTTP: Funcionalidades que provee el protocolo#30|30]]
	- [[#HTTP: Funcionalidades que provee el protocolo#31|31]]
- [[#HTTP: Entity tags, y caching|HTTP: Entity tags, y caching]]
	- [[#HTTP: Entity tags, y caching#32|32]]
	- [[#HTTP: Entity tags, y caching#33|33]]
	- [[#HTTP: Entity tags, y caching#34|34]]
	- [[#HTTP: Entity tags, y caching#36|36]]
	- [[#HTTP: Entity tags, y caching#37|37]]
	- [[#HTTP: Entity tags, y caching#40|40]]
- [[#Clientes DNS|Clientes DNS]]
	- [[#Clientes DNS#41|41]]
		- [[#41#IP's|IP's]]
		- [[#41#Autoridades|Autoridades]]
					- [[#ACA|ACA]]
	- [[#Clientes DNS#42|42]]
	- [[#Clientes DNS#43|43]]
	- [[#Clientes DNS#44|44]]
	- [[#Clientes DNS#45|45]]
- [[#DNS y HTTP|DNS y HTTP]]
	- [[#DNS y HTTP#46|46]]
	- [[#DNS y HTTP#47|47]]
	- [[#DNS y HTTP#Configuración de DNS Server|Configuración de DNS Server]]

# 1
## E1. 
```bash
find /var/log/ | grep boot | xargs grep boot | cut -d: -f1 | uniq| xargs tail -f
```
- [[Comandos#Encontrar archivos]]
- [[Comandos#Redireccionar salida a otro archivo]]
- [[Comandos#tail Para ver los cambios en ese archivo]]
- [[Comandos#find Encontrar archivos]]
- [[Comandos#xargs Para agregar mas argumentos]]

- `xargs` agarra el output de la izquierda y so lo mete como argumento a la derecha (`grep boot`)
- En este caso `cut -d: -f1` corta la linea en el primer trozo de texto (f1, f2 si queremos el segundo, fn si el n-ésimo) antes del ':' (-d delimitador).

## E2.
![[Pasted image 20230806112732.png]]

El 1 no frenaba nunca (no llegue a verlo frenar). A medida que el buffer se agranda, más rápido es. La diferencia de tiempos es porque mientras más grande el buffer, mayor información se copia por momento. Entonces un buffer de 1 toma mucho porque se copia 1 byte a la vez, un buffer de 4MB ya es un poco más rápido. 
La ventaja de sendfile es
![[Pasted image 20230806113318.png]]


## E3.

> ¿Cómo se codifica los caracteres en un documento texto plano?¿Qué diferencias entre las codificaciones ASCII, ISO-8859-1, UNICODE? ¿Cuales son su ventajas y desventajas?

Se codifican usando alguna convención tipo ASCII o esas que se mencionan (convierten numeros en dibujitos de caracters). Las diferencias es que en ASCII (el original 1.0) está muy limitadode caracteres, tiene pocos bytes de espacio para representar caracteres, el ISO-8859-1![[Pasted image 20230806113807.png]] y despues el unicode (UCS, universal character set de 32-bit) combina todos los estándares, tiene todos y puede hacer combinaciones entre caracteres.
Ventajas dependen de que tan grande querés el archivo, o que tantas letras específicas querés usar, emojis etc.

## E4. 
> ¿Es lo mismo hablar de UNICODE y de UTF-8? ¿son conceptos que refieren a diferentes cosas?

Unicode se refiere al conjunto de caracteres y sus asignaciones de puntos de código, mientras que UTF-8 es una forma particular de codificar esos caracteres en bytes para su almacenamiento o transmisión en sistemas informáticos. Unicode define los caracteres y sus identificadores, y UTF-8 define cómo esos caracteres se representan en memoria o en archivos.
### Unicode
Unicode es un estándar de codificación de caracteres que asigna un número único (llamado "punto de código") a cada carácter de escritura utilizado en la mayoría de los sistemas de escritura del mundo. El objetivo de Unicode es proporcionar una forma unificada de representar y manejar caracteres de diferentes idiomas y sistemas de escritura en sistemas informáticos. Por ejemplo, la letra "A" se representa en Unicode con el punto de código U+0041.

### UTF-8
UTF-8 (Unicode Transformation Format 8-bit) es una codificación de caracteres específica que se utiliza para representar los puntos de código Unicode en forma de secuencias de bytes. Es una de las muchas formas de representar caracteres Unicode en datos binarios. UTF-8 es especialmente popular en la web y en sistemas informáticos modernos debido a su capacidad para representar todos los caracteres Unicode de manera eficiente y su compatibilidad con ASCII (los primeros 128 caracteres de Unicode son iguales a los caracteres ASCII estándar).

## E5.
> ¿Qué criterio utilizaría para decidir utilizar UTF-8, UTF-16 o UTF-32?

Si el almacenamiento es limitante. El rango decaracteres que quiero utilizar.

## E6.
Cuando ejecutas este código en Java, imprimirá un emoji en la consola y luego mostrará la longitud de la cadena. El emoji en cuestión es 🍕 (una rebanada de pizza).

La longitud de la cadena es 2, lo que parece incorrecto considerando que el emoji se muestra como un único carácter. Esto se debe a que el emoji 🍕 está representado por un único punto de código Unicode (U+1F355), pero la forma en que se codifica en UTF-16 (la codificación de caracteres predeterminada en Java) requiere dos unidades de código UTF-16 para representarlo completamente.

## E7.
La auto-sincronización significa que es posible identificar el comienzo de un carácter o un punto de código en una secuencia de bytes sin tener que analizar todo el contenido anterior. En otras palabras, cada punto de código Unicode está codificado de tal manera que su inicio se puede reconocer fácilmente, y no es necesario decodificar todo el contenido previo para llegar a un punto específico.

Esto es una ventaja en el acceso aleatorio de datos porque permite:
1. Eficiencia en Búsqueda: Si estás buscando un carácter o un punto de código específico dentro de una secuencia, puedes moverte directamente a una ubicación cercana en la secuencia y comenzar a decodificar desde allí. No es necesario comenzar desde el principio y decodificar cada carácter previo.
2. Eficiencia en Decodificación: Cuando se accede a un punto de código en particular, solo se necesita decodificar ese punto de código y no es necesario decodificar todo el contenido previo.
## E8.
Basicamente discuten como se almacena la info en bytes ordenades  de una forma u otra. 
### Little Endian
El byte menos significativo (el byte más pequeño) de un número multibyte se almacena en la dirección de memoria más baja, mientras que los bytes más significativos se almacenan en direcciones de memoria más altas. Es decir, los bytes se almacenan en orden inverso al de su importancia en la representación numérica. La arquitectura x86 y x86-64, utilizada en la mayoría de las computadoras personales, es un ejemplo de arquitectura Little-Endian.

### Big Endian
El byte más significativo (el byte más grande) se almacena en la dirección de memoria más baja, mientras que los bytes menos significativos se almacenan en direcciones de memoria más altas. En otras palabras, los bytes se almacenan en el mismo orden en que se representarían numéricamente. Algunas arquitecturas como PowerPC y SPARC utilizan el formato Big-Endian.

## E9.
### Archivos de Texto Plano
Los archivos de texto plano contienen datos legibles por humanos y están compuestos principalmente de caracteres de texto. Estos archivos pueden contener letras, números y símbolos en un formato legible y generalmente se almacenan utilizando una codificación de caracteres específica, como ASCII o UTF-8.

### Archivos Binarios 
Los archivos binarios contienen datos en una forma que no está destinada a ser legible directamente por humanos. Pueden contener una amplia variedad de datos, como imágenes, videos, ejecutables, datos comprimidos, etc. Los archivos binarios no están limitados a caracteres de texto y se almacenan en su forma cruda. Por ejemplo imagenes, audios, .exe, otros

## E10.

### Métodos de Serialización (como está la info)
- **Serialización en formato binario**: En esta técnica, los datos se almacenan en el archivo en su representación binaria directa. Puedes usar las funciones `fwrite()` y `fread()` en C para escribir y leer datos en formato binario. Esta técnica es eficiente en términos de almacenamiento y velocidad de lectura/escritura, pero los archivos resultantes no son legibles para los humanos.
- **Serialización en formato de texto plano**: Los datos se almacenan en el archivo en un formato de texto legible para los humanos. Puedes usar funciones como `fprintf()` y `fscanf()` para escribir y leer datos en formato de texto. Aunque esta técnica produce archivos legibles, puede ser menos eficiente en términos de almacenamiento y velocidad.
- **Serialización en formato JSON**: JSON (JavaScript Object Notation) es un formato de texto que es ampliamente utilizado para intercambiar datos estructurados. Puedes utilizar bibliotecas como `json-c` o `json-cpp` para serializar y deserializar tus estructuras en formato JSON. Esta técnica ofrece una combinación de legibilidad humana y eficiencia.
- **Serialización en formato XML**: XML (eXtensible Markup Language) es otro formato de texto utilizado para representar datos estructurados. Puedes utilizar bibliotecas como `libxml2` para trabajar con XML en C. Sin embargo, XML tiende a ser más verboso en comparación con JSON.

### Null terminated vs chunked
#### **Codificación Null-terminated**
En esta técnica, el "string" se almacena como una secuencia de caracteres, seguida por un carácter nulo (byte 0). Por lo tanto, la longitud del "string" no se almacena explícitamente, y la cadena se considera completa cuando se encuentra el carácter nulo. Esta técnica es simple y eficiente en términos de almacenamiento, ya que no requiere almacenar la longitud por separado. Sin embargo, presenta desventajas si los datos pueden contener caracteres nulos legítimos, lo que podría llevar a confusiones al interpretar el "string".

Ventajas de la codificación Null-terminated:

- Eficiente en almacenamiento (no se necesita almacenar la longitud por separado).
- Fácil de trabajar con cadenas de caracteres en lenguajes de programación que manejan cadenas "null-terminated" de manera nativa (como C).

Desventajas de la codificación Null-terminated:

- Problemas con caracteres nulos legítimos dentro del "string".
- Necesita buscar el carácter nulo para determinar la longitud.

#### **Codificación chunked (por bloques)**
En esta técnica, primero se almacena la longitud del "string" y luego se almacenan los bytes que componen el "string". La longitud se almacena en un formato determinado, como un número fijo de bytes o una codificación Null-terminated para la longitud.

Ventajas de la codificación chunked:

- Evita problemas con caracteres nulos dentro del "string".
- Permite trabajar con datos binarios sin preocuparse por caracteres nulos.

Desventajas de la codificación chunked:

- Puede requerir más almacenamiento debido a la longitud adicional almacenada.
- Requiere un paso adicional para leer la longitud antes de leer los datos reales.

## 12
La parte de "secition-14.19" se llama [[URI#Fragmento]] y no se envía por la red al hacer la solicitud (request) al servidor. El fragmento es una parte de la URI que se maneja únicamente en el lado del cliente (navegador web). Cuando el navegador recibe la respuesta del servidor y carga el recurso, el fragmento se utiliza para desplazarse directamente a la parte correspondiente del recurso en la página web.

## 13
1. **URI (Identificador de Recursos Uniforme):** Una URI es una cadena de caracteres que se utiliza para identificar de manera única un recurso en Internet. Puede representar una página web, un archivo, un servicio, etc. Las URIs son las direcciones que utilizamos para acceder a recursos en la web. Ejemplos de URIs son las URL (Localizadores de Recursos Uniformes) y las URN (Nombres de Recursos Uniformes).
2. **URI reference (Referencia de URI):** Una URI reference es una cadena de caracteres que se utiliza para hacer referencia a una URI completa o parcial. Una URI reference puede ser más flexible y no necesariamente completa. Incluye los componentes de una URI (como esquema, autoridad, ruta, consulta y fragmento) pero puede faltar uno o más de estos componentes. Las URI references se utilizan en contexto donde se necesita un enlace o referencia a un recurso, pero no es necesario proporcionar toda la información.

## 14
![[Pasted image 20230809085104.png]]


## 15
```bash
http://

abc.com:80
ABC.com
ABC.com:

/~smith/home.html
/%7Esmith/home.htm
/%7esmith/home.htm
```

## 16
-

## 17
```bash
nc -l -p 12345
```
```bash
nc <IP-terminal> 12345
hola
```
`<IP-terminal> = 127.0.0.1`


## 18
```bash
echo -e "hola \r\n como \r\n es \r\n tan" | nc 127.0.0.1 12345
```

## 19


### a 
Cuando un User Agent (como un navegador web) envía una solicitud HTTP a un servidor, el request contiene una serie de encabezados (headers) que proporcionan información adicional sobre la solicitud. 
	 - `nc -l -p 9090`
	 - entro a http://localhost:9090/
	 - Obtengo en el listener ![[Pasted image 20230809092424.png]]
	 	 - Vease que el User-Agent indica el navegador web y el SO

### b, c
En este ejemplo vemos como enviar correctamente 
`echo -e "HTTP/1.1 200 OK\r\nContent-Length: 12\r\n\r\nHello, world" | nc -l -p 9090`
![[Pasted image 20230809092044.png]]
Si ahora yo hago 
`echo -e "Hello, world" | nc -l -p 9090`
![[Pasted image 20230809093238.png]]
![[Pasted image 20230809093501.png]]


## 20
```bash
echo -e "GET / HTTP/1.1\r\n\r\n" | nc www.google.com.ar 80
```
### A
El código de respuesta del servidor es "200 OK", significa que el pedido fue procesado y entendio (el GET). El encabezado requerido que debe estar presente en la respuesta es **Content-Type**, que indica el tipo de contenido que se está devolviendo.

Acá el header de respuesta:![[Pasted image 20230813182429.png]]
### B
```bash
echo -e "GET /search HTTP/1.1\r\nHost: www.google.com.ar\r\n\r\n" | nc www.google.com.ar 80
```
```bash
HTTP/1.1 302 Found
Location: http://www.google.com.ar/webhp
Cache-Control: private
Content-Type: text/html; charset=UTF-8
Content-Security-Policy: object-src 'none';base-uri 'self';script-src 'nonce-q8nnim2M5ICW-iWWX9kT7Q' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/xsrp
P3P: CP="This is not a P3P policy! See g.co/p3phelp for more info."
Date: Sun, 13 Aug 2023 21:25:53 GMT
Server: gws
Content-Length: 227
X-XSS-Protection: 0
X-Frame-Options: SAMEORIGIN
Set-Cookie: 1P_JAR=2023-08-13-21; expires=Tue, 12-Sep-2023 21:25:53 GMT; path=/; domain=.google.com.ar; Secure
Set-Cookie: AEC=Ad49MVETtrsatuYGEWoSUy4UQiSySU3mdv5Fl8iQS8zULGk74fKgAukwArY; expires=Fri, 09-Feb-2024 21:25:53 GMT; path=/; domain=.google.com.ar; Secure; HttpOnly; SameSite=lax
Set-Cookie: NID=511=kaRO97Zp2m-cuMsP_RN4XnR0i9bXaPegDatXk6JcByVgV5gEc0egD9k31WrWOoQUIywh3fXqNU59EE3I0V7y4DaOjqMRR6U5q66gfGwUL5aEp_rc-6O412AgprurR-FD7gdVapcmnABFtiAlEk7T5p__3QEScuJ6uIVsbn2eec4; expires=Mon, 12-Feb-2024 21:25:53 GMT; path=/; domain=.google.com.ar; HttpOnly

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>302 Moved</TITLE></HEAD><BODY>
<H1>302 Moved</H1>
The document has moved
<A HREF="http://www.google.com.ar/webhp">here</A>.
</BODY></HTML>
```
- **TTP/1.1 302 Found**: This is an HTTP status code indicating that the requested resource has been temporarily moved to a new location. In this case, it's a "302 Found" response which typically signifies a redirection.
    
- **Location: [http://www.google.com.ar/webhp](http://www.google.com.ar/webhp)**: This header specifies the new location where the requested resource can be found. In this case, it's indicating that the resource has been moved to "[http://www.google.com.ar/webhp](http://www.google.com.ar/webhp)".
    
- **Cache-Control: private**: This header indicates that the response is intended for a single user and shouldn't be cached by intermediate proxies or caches.
    
- **Content-Type: text/html; charset=UTF-8**: This header specifies the type of content being returned in the response. In this case, it's HTML content with the character encoding set to UTF-8.
    
- **Content-Security-Policy**: This header provides security policies for controlling which resources can be loaded on the page. It restricts the sources of objects, scripts, and other resources that can be used.
    
- **Date**: The date and time the response was generated.
    
- **Server**: The name of the web server that generated the response. In this case, it's "gws," which stands for Google Web Server.
    
- **X-XSS-Protection**: This header indicates whether the browser's built-in XSS protection should be enabled. "0" means it's disabled.
    
- **X-Frame-Options: SAMEORIGIN**: This header prevents the page from being displayed in a frame or iframe on a different domain.
    
- **Set-Cookie**: These headers indicate that cookies are being set. Cookies are used to store data on the user's browser.
    
- **HTML**: The HTML content of the response body. It's a simple HTML page that informs the user that the document has moved and provides a link to the new location.


## 21
**cURL** a diferencia de **wget** tiene mayor abarcabilidad en cuanto a la interaccion con el servidor. Por ejemplo `curl` puede usar GET y POST. `wget` se usa para descargar cosas de internet sin tanta complejidad.

CURL + 
- `-0` indica que se usa HTTP 1.0
- `--http1.1` indica que se use 1.1
- `--http2` indica que se use 2
- `--compressed` indica a curl que descomprima si esta comprimido
- `-d` los datos del body de un POST
- `-H` header
- `-i`Muestra tanto los encabezados de respuesta como el contenido en la salida.
- `-s` solo muestra la salida si hubo un erro, (silecionso)
- `--socks5` Permite especificar un servidor proxy SOCKS5 para enrutar las solicitudes a través de él.


## 22
![[Pasted image 20230813185005.png]]

![[Pasted image 20230813185101.png]]

Fijarse en la sutil diferencia que en el primer HTTP request se retorna 200 OK y se empieza a descargar, en cambio en el --continue, retorna 206 Partial Content, que indica que la respuesta ya no es el iso entero sino solo la parte que falta.


# HTTP: Funcionalidades que provee el protocolo


## 23
El protocolo HTTP especifica que el header en su totalidad es case insensitive. Entonces sí, son equivalentes.

## 24
1. Chunked significa que la información en el body está fragmentada y por ejemplo. **Permite que el contenido se transmita mientras se genera, en lugar de esperar a que se complete todo el contenido antes de enviarlo**.
	1. Por ejemplo 
```makefile
HTTP/1.1 200 OK
Content-Type: text/plain
Transfer-Encoding: chunked

25
Este es el primer trozo.
1A
Este es el segundo trozo.
0
```

2. Otras codificaciones
	1. gzip: contenido comprimito con DEFLATE
	2. deflate : parecido al anterior
	3. binario
	4. brotoli, mejor que gzip en compresion pero mas lento
	5. identity, la default sin compresión ni codificacion, nada raro.


3. Sirven para mandar contenido dependiendo de cuál es la utilidad posible. Que es esta pregunta man. Si vos queres un jueguito re pesado mandarás la data comprimida, si queres descargar cosas sin saber su tamaño vas por chunked y así cada caso es diferente.
4. Eeeeeee
5. Cada tipo de codificación tiene un propósito específico y se utiliza en función de las necesidades de transmisión de contenido, eficiencia y compatibilidad con los agentes de usuario.

## 25

### ¿Qué es un media type?
> Los media types proporcionan una forma estandarizada de comunicar el tipo de contenido entre diferentes sistemas y aplicaciones, lo que facilita la correcta interpretación y manejo de los datos en el entorno de la web.

- Un media type o MIME type es una etiqueta para identificar a un recurso de internet. 
- Se usa para para entender como debe manejarse el contenido y que los navegadores o servidores sepan como mostrar la información. 
Cada MIME type tiene 2 partes, el **tipo**(1) y el  **subtipoe**(2). Primero:
- text
- image
- audio
- video
- application
- multipart
Segundo:
- text/html
- text/xml
- image/jpg
- image/png

## 26

### A
Se necesita que tanto el cliente como el servidor tiene que tener los encabezados (headers) correctos

### B
Ventajas de HTTP vs NO HTTP

- **Reducción de latencia** una conexión http puede mantener abierta una sesión durante un rato para que la apertura y el "handshake" entre cliente y servidor sea uno solo.
- **Menor sobrecarga de red**: Con conexiones persistentes, se evita la sobrecarga de establecer una conexión nueva para cada solicitud. Esto resulta en un uso más eficiente de los recursos de red y reduce la congestión en la red.
- **Mejora de rendimiento**: La capacidad de enviar múltiples solicitudes antes de esperar las respuestas individuales (mediante pipelining) permite una mejor utilización de la conexión y reduce el tiempo de inactividad mientras se espera una respuesta. Esto mejora el rendimiento general de las solicitudes y respuestas.
- **Ahorro de recursos del servidor**: Las conexiones persistentes permiten que el servidor maneje varias solicitudes a través de la misma conexión, lo que reduce la carga en términos de establecimiento y cierre de conexiones. Esto ahorra recursos del servidor y mejora su capacidad para manejar un mayor número de solicitudes.
- **Eficiencia en navegadores**: Los navegadores modernos aprovechan las conexiones persistentes para cargar recursos como imágenes, hojas de estilo y scripts de manera más eficiente, ya que pueden reutilizar conexiones existentes para cargar elementos de la página.

### Pipelining
> El pipelining es una técnica que se usa junto con las conexiones persistentes para mejorar aún más la eficiencia en la transferencia de datos. Con el pipelining, un cliente puede enviar múltiples solicitudes al servidor antes de recibir las respuestas correspondientes. Esto permite que las solicitudes se envíen secuencialmente a través de la misma conexión sin esperar las respuestas intermedias, lo que reduce el tiempo total de transferencia.

Sin embargo, es importante tener en cuenta que el pipelining no es ampliamente utilizado debido a ciertas limitaciones y problemas potenciales, como la posibilidad de bloqueo en la transferencia si una solicitud tiene problemas y las respuestas no coinciden en orden. En su lugar, se han desarrollado enfoques más sofisticados como el multiplexado HTTP/2, que resuelven estos problemas y ofrecen un rendimiento mejorado en comparación con el pipelining.

## 27
El protocolo HTTP porevee:
- GET
- POST
- HEAD
- DELETE
- OPTIONS
- TRACE
- PUT

Se dice idemoptente a los métodos que al ser ejecutados no cambian el estado en reiteradas peticiones, por ejemplo si hago get de un recurso varias veces, el accionar de get no afecta en ningun sentido la respuesta y siempre se va a obtener la misma respuesta luego de varias peticiones. En cambio POST puede no obtener la misma respuesta siempre pues el POST permite envíar un body que cambia la respuesta del receiver.

En el siguiente caso
> Se cuenta con una extensión al user-agent (ej: plugin de Firefox) que
una vez cargada las página web (de formato HTML) el mismo recolecta
todos los links en el documento, y con el objetivo de acelerar la expe-
riencia del usuario, comienza a descargar todos los links recolectados.
De esta forma el usuario cuando siga algún link de interés no tendrá
que esperar. Suponga que el usuario visita un sitio web que tiene una
página web que presenta un listado de cosas, y cada ítem, además de
presentar su nombre, presenta un link para editar su contenido, y otro
link para eliminar el mismo (es decir el clásico ABM). El desarrollador
decidió que realizando un GET a los link de eliminación (/items/123/
delete).

el GET no es idempotente pues está elimiando un recurso

1. Si el usuario tiene acelerador de internet activado, va a empezar a descargar el recurso varias veces porque piensa que es idempotente porque esa es la naturaleza del GET
2. El que hizo el GET tiene la culpa
3. Se puede solucionar haciendo un DELETE en vez de un GET.

El método HTTP DELETE se considera idempotente. La idempotencia se refiere a la propiedad de una operación en la que realizar la misma solicitud múltiples veces produce el mismo resultado que hacerlo solo una vez. En el caso del método DELETE, si se realiza una solicitud DELETE varias veces sobre el mismo recurso, el resultado seguirá siendo el mismo: el recurso será eliminado.

## 28
Me tira (405) Method not Allowed.

## 29
- Que código de retorno utilizaría desde su aplicación web para las siguientes situaciones?

### 302 Found
a. El recurso al que se está accediendo ya no se encuentra en la dirección a la que se está intentando acceder. Se conoce cual es la nueva dirección que se debe utilizar a partir de este momento.
302

### 403  Forbidden
b. El cliente no tiene permiso para acceder a la página (ejemplo un usuario anónimo encontró cual es la URL del backoffice de administración)

### 405 Not allowed
b.b Cuando se usa un metodo no soportado

### 401 Unauthorized
c. El cliente no se encuentra autenticado
El cliente está enviando un DELETE al recurso pero esa operación no es soportada (solo soporta el GET).
### 409 Conflict
d. El recurso que se está editando (por ejemplo una entrada de un blog) fue editado desde el momento que nosotros lo comenzamos a editar, y apretamos el botón guardar (no queremos perder los cambios recién guardados)

### 410 Gone
Eliminado premanentemente y no será recuperado

### 404 Not Found
Se utiliza cuando el servidor no puede encontrar el recurso solicitado en el momento, pero no está seguro si el recurso se eliminará permanentemente o si podría estar disponible en el futuro.

### 400 Bad request
f. Faltó en la URL de un GET un parámetro (ej /foo/bar?param=123
g. El formato de un parámetro es incorrecto (ej /foo/bar?param=abc donde param debía ser un número entero).

### 415 Unsuported Media Type
Se está intentando subir un recurso cuyo formato no es soportado en el servidor

### 503 Service Unavailable
El recurso al que se está intentando acceder requiere de otro sistema externo que no se encuentra por el momento disponible (ej: está caído)


## 30

```HTTP
GET / HTTP/1.1
Authorization: Basic YWxndW51c3VhcmlvOmFsZ3VuYXBhc3N3b3Jk
```

Este request indica que hay una autenticación. Cuando la autenticación es Basic el contenido esta codificado en base 64, el usuario seguido por la contraseña separados por un ";".
El código de la autorización una vez "decoded" dice : "algunusuario:algunapassword". Lo hice con un [base 64 decoder online](https://www.base64decode.org/).

## 31
HTTP ofrece:
- keep-alive
- cache
- comprecion
- pipeline
- Chunked
- otros...
Para minimizar el tráfico de red y la utilización de los recursos.

# HTTP: Entity tags, y caching
## 32 
Haga un GET condicional utilizando la fecha de última modificación
```bash
curl -I --header "If-Modified-Since: Tue, 01 Jan 2023 00:00:00 GMT" http://foo.leak.com.ar/
```
Haga un GET condicional utilizando los “entity tags”
```bash
curl -I --header "If-None-Match: \"12345\"" http://foo.leak.com.ar/
```

## 33
¿Qué interpretará un UA que tiene soporte de caching si recibe en una respuesta el header
Cache-Control: max-age=3600, must-revalidate

Lo que interpreta un UA es que si el recurso tiene mayor a 3600 (unidad de tiempo) entonces tiene que mantenerse en el cache sino, se saca del cache y se lo vuelve a buscar al servidor. el must-revalidate para checkear si hubo un update, se le hace un pequeño request al servidor y si responde 304 Not Modified entonces devuelve el  guardado en cache. Caso contrario va a buscar al servidor nuevamente la respuesta actualizada y se la guarda en cache.

## 34


## 36

```nginx
server {
        listen 80;
        listen [::]:80;


        root /var/www/html/foo;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name foo;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
        }

}
```

## 37
[NGINX - Doc](http://nginx.org/en/docs/beginners_guide.html)
[NGINX - Directives](http://nginx.org/en/docs/http/ngx_http_proxy_module.html)


## 40
[NGINX- GZIP](http://nginx.org/en/docs/http/ngx_http_gzip_module.html#gzip)
Agregar la directiva `gzip on;`  a los servers y listo.

a. Obvio que las ventajas están en la particularidad de que es un archivo comprimido entonces pesa menos, las cosas cargan más rápido.

b. La compresión de recursos puede tener un impacto en el rendimiento del servidor, ya que necesita comprimir los archivos antes de enviarlos. Sin embargo, este impacto suele ser insignificante en comparación con los beneficios de la compresión.

c. 
- Sí, la compresión de recursos puede ahorrar ancho de banda, ya que los archivos se envían en un formato más compacto. Esto es especialmente beneficioso para usuarios con conexiones lentas o limitadas.
- La mejora en la velocidad de carga de la página debido a la compresión también puede aumentar positivamente la experiencia del usuario, ya que las páginas se cargarán más rápidamente.

d.
Algunas ventajas de utilizar Tomcat para servir contenido incluyen:
- **Soporte para aplicaciones Java:** Tomcat es un contenedor web diseñado para ejecutar aplicaciones Java, lo que es útil si estás desarrollando aplicaciones Java o basadas en Java.
- **Gestión de servlets y JSP:** Tomcat es capaz de manejar servlets y JavaServer Pages (JSP), lo que permite construir aplicaciones web dinámicas y escalables.
- **Configuración avanzada:** Tomcat ofrece una configuración más específica para aplicaciones Java, lo que puede ser esencial para aplicaciones complejas.

# Clientes DNS

## 41
`dig NS example.com`


### IP's
![[Pasted image 20230820130254.png]]

###  Autoridades
![[Pasted image 20230820155942.png]]

###### ACA
![[Pasted image 20230820160109.png]]
- `it.itba.edu.ar.`: Esta es la zona de nombres a la que se refiere la respuesta. Indica que la respuesta está relacionada con la configuración de la zona de nombres `it.itba.edu.ar`.
- `300`: Este es el valor de TTL (Time-to-Live) en segundos. Indica cuánto tiempo esta información debe mantenerse en caché en los servidores DNS antes de consultar nuevamente el servidor de nombres para obtener información actualizada.
- `IN`: Indica que estamos hablando de una entrada en el espacio de nombres de Internet (Internet Namespace).
- `SOA`: Representa el tipo de registro, que es un registro de Start of Authority (SOA). Este tipo de registro contiene información fundamental sobre la zona de nombres.
- `crystal.it.itba.edu.ar.`: Este es el servidor de nombres primario (primary name server) autoritativo para la zona de nombres `it.itba.edu.ar.`. Es el servidor que tiene la autoridad final sobre la configuración de esta zona.
- `root.crystal.it.itba.edu.ar.`: Esta es la dirección de correo electrónico del administrador de la zona (administrative email). Indica que el administrador de esta zona es `root@crystal.it.itba.edu.ar`.
-  `2023061300`: Este es el número de serie del SOA. Indica cuándo se realizó la última actualización en esta zona de nombres. La convención de formato es `AAAAJJJNN`, donde `AAAA` es el año, `JJJ` es el día del año y `NN` es el número de la actualización en ese día.
    
- `3600`: Este es el valor de refresh (cada cuánto tiempo se debe actualizar la información) en segundos.
    
- `7200`: Este es el valor de retry (cada cuánto tiempo se debe reintentar la conexión en caso de fallar) en segundos.
    
- `2419200`: Este es el valor de expire (tiempo máximo que los servidores pueden mantener la información en caché antes de considerarla obsoleta) en segundos.
    
- `86400`: Este es el valor de minimum (valor mínimo de TTL que debe aplicarse a otros registros) en segundos.

## 42
`dig MX example.com`

![[Pasted image 20230820161703.png]]
![[Pasted image 20230820161722.png]]
![[Pasted image 20230820161740.png]]

## 43
Los servidores de nombre que entran en juego son como se pueden ver [[#ACA]]


## 44
`dig +trace NS pampero.it.itba.edu.ar`

## 45
`whois example.com`
preguntar por seguridades permitidas en clarin vs apple


# DNS y HTTP
## 46
En `/etc/nginx/sites-available` creo un archiv gooLeak.
```nginx
server {
        listen 80;
        listen [::]:80;
        server_name foo.pdc.lab;


        location / {
                proxy_pass http://foo.leak.com.ar/;
        }

}
```

en `/etc/nginx/sites-enabled` tiro un `ln -s /etc/nginx/sites-available fooLeak` para crear el link simbólico.

Voy a `/etc/hosts` y agrego una linea `127.0.0.1  foo.pdc.lab` . Restarteo nginx y puedo testear que funciona haciendo `curl http://foo.pdc.lab` .

## 47
```nginx
server {
        listen 80;
        listen [::]:80;
        server_name foo.pdc.lab;


        location / {
                #proxy_pass http://foo.leak.com.ar/;
                rewrite ^(.*)$ http://foo.leak.com.ar$request_uri;
        }

}
```


# Configuración de DNS Server

## 48 

Para ver los logs `journalctl -f` .
Se puede configurar las zonas en named.conf definiendo la zona que va a ser utilizada que está especificada en /etc/bind/zones.

## 53


# SMTP

## 54
Si quiero enviar de forma directa un correo electrónico a una casilla del dominio itba.edu.ar. tengo que conectarme a los servidores que me da `dig +short MX itba.edu.ar.` . En donde en realidad tengo que agarrar el de prioridad más alta.

`dig +short MX itba.edu.ar | sort -n`

## 55
![[Pasted image 20230830202347.png]]
No puedo porque tengo el IP bloqueado
![[Pasted image 20230830202829.png]]


### Relay
Una configuración de relay es un servidor que recibe correos y los envía a su destinatario. Actúa como intermediario o sea que es un poco parecido a un proxy. Por seguridad también puede ser implementado.


## 56

`mailq` nos deja fijarnos los mails en la cola para enviar.

Si quiero mandar los logs a otro lado, agrego a main.cf

	`maillog_file=/var/log/postfix.log`


## 60 
 
### SPF (Sender Policy Framework):

**Ventajas:**
- **Validación de Origen:** SPF ayuda a verificar si el servidor que envía un correo electrónico tiene permiso para enviar mensajes en nombre del dominio especificado.
- **Reducción de Spoofing:** Ayuda a prevenir el envío de correos electrónicos falsificados desde direcciones de dominio legítimas.
- **Fácil Implementación:** SPF es relativamente fácil de configurar en los registros DNS del dominio.
    
**Desventajas:**
- **No Evita Totalmente el Spam:** SPF no elimina directamente el spam, solo ayuda a detectar direcciones de remitente falsificadas.
- **Requiere Mantenimiento:** Si se implementa incorrectamente, los correos legítimos pueden ser marcados como spam.
- **No Aborda el Contenido:** SPF no tiene en cuenta el contenido del correo electrónico.

### DomainKeys (o DKIM - DomainKeys Identified Mail):
**Ventajas:**
- **Autenticación y Firma:** DKIM firma los correos electrónicos con una clave criptográfica, lo que permite a los servidores de destino autenticar el correo electrónico.
- **Reducción del Spoofing:** Similar a SPF, ayuda a prevenir la falsificación de remitentes.
- **Mejora la Entrega:** Los correos con firma DKIM tienen una mayor probabilidad de ser entregados en la bandeja de entrada.
    **Desventajas:**
- **Configuración Compleja:** Configurar DKIM puede ser complejo, especialmente en organizaciones grandes.
- **Necesita Mantenimiento:** Las claves DKIM deben ser rotadas y administradas adecuadamente.
### Grey Listing:

**Ventajas:**
- **Efectivo contra Spammers Automáticos:** Los spammers automatizados a menudo no reintentan enviar correos después del primer intento fallido.
- **Reduce el Volumen de Spam:** Puede reducir significativamente la cantidad de correos basura que llegan a la bandeja de entrada.
**Desventajas:**   
- **Retraso en la Entrega:** La técnica de Grey Listing puede causar retrasos en la entrega legítima de correos electrónicos, ya que los servidores deben reintentar el envío.
- **No Efectivo contra Spammers Persistentes:** Los spammers que reenvían automáticamente el correo pueden sortear esta técnica.


### Filtros Bayesianos:
**Ventajas:**
Aprendizaje Automático:** Los filtros Bayesianos pueden adaptarse y aprender de las características de los correos electrónicos a lo largo del tiempo.
    - **Flexibilidad:** Pueden ser altamente personalizables según las preferencias del usuario.
    - **Identificación de Contenido Malicioso:** Pueden ayudar a identificar contenido malicioso, no solo spam.
    
Desventajas:

- **Falsos Positivos/Negativos:** Puede haber casos donde los correos legítimos sean marcados como spam (falsos positivos) o donde el spam pase desapercibido (falsos negativos).
 - **Dependencia del Entrenamiento:** La precisión de los filtros Bayesianos depende de la calidad y cantidad del conjunto de entrenamiento.

Cada técnica tiene sus propias ventajas y desventajas, y a menudo, las soluciones anti-spam efectivas combinan varias técnicas para mejorar la detección y reducir tanto el spam como los falsos positivos.


## 61
`dig +short TXT itba.edu.ar`
En la salida se puede ver la versión spf usada y los ips que pueden envíar mail y las ips autorizadas por algunos dminios conocidos.

makefile

```c
v=spf1 include:_spf.google.com ip4:190.104.250.100 ip4:190.104.250.101 ip4:52.67.50.43 ip4:54.94.246.207 ip4:52.67.178.216 ip4:52.67.194.156 ip4:200.32.57.124 include:spf.perfit-mail.net include:spf.mandrillapp.com include:_spf.embluemail.com include:mh.blackboard.com ~all
```


- `v=spf1`: Indica la versión 1 del estándar SPF.
    
- `include:_spf.google.com`: Indica que se deben incluir las direcciones IP autorizadas del dominio `_spf.google.com`.
    
- `ip4:190.104.250.100`, `ip4:190.104.250.101`, ...: Estas son direcciones IPv4 específicas que están autorizadas para enviar correos electrónicos en nombre del dominio. Cualquier servidor que tenga una de estas direcciones IP puede enviar correos en nombre del dominio.
    
- `include:spf.perfit-mail.net`, `include:spf.mandrillapp.com`, ...: Similar al caso de Google, estos son otros dominios cuyas direcciones IP autorizadas están permitidas para enviar correos electrónicos en nombre del dominio.
    
- `~all`: Esta es una directiva que indica la política de SPF. El símbolo tilde (~) seguido de `all` significa que las direcciones IP que no coincidan con ninguna de las reglas anteriores "fallarán suavemente". En otras palabras, los correos electrónicos enviados desde direcciones IP no autorizadas no serán rechazados de inmediato, pero pueden ser tratados como posibles correos no deseados.

# Codificaciones BASE

## 62
convertimos las letras en binario

- H = 72
- O = 79
-  = 32
- L =76
- A =65
Entonces
- 1001000
- 1001111
- 100000
- 1001100
- 1000001

y despues codifico a base64

SE8gTEE=

## 63

chau

## 64
