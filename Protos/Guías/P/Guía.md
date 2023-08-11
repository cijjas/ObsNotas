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
