[Drive de la materia (Material)](https://drive.google.com/drive/u/1/folders/1IzoSBcLlCac7pMZcgjdvKrKyLSdobenA)

![[guia-practica-r0.pdf]]

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