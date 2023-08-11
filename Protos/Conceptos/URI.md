# URI
> Un URI es una cadena de caracteres que se utiliza para identificar un recurso en Internet de manera única. Puede representar una página web, una imagen, un archivo, un servicio, entre otros. Los URIs se utilizan para acceder a recursos en la web y proporcionar una forma estándar de identificarlos.

> Un **identificador de recursos uniforme** o **URI** —del inglés _uniform resource identifier_— es una cadena de caracteres que identifica los recursos –físicos o abstractos– de una red de forma unívoca. La diferencia respecto a un [localizador de recursos uniforme](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme "Localizador de recursos uniforme") ([[URI#URL]]) es que estos últimos hacen referencia a recursos que, de forma general, pueden variar en el tiempo.

![[Pasted image 20230808171039.png]]

Un URI consta de las siguientes partes 
![[Pasted image 20230808171145.png]]
## Esquema
nombre que se refiere a una especificación para asignar los identificadores, e.g. `urn:`, `tag:`, `cid:`. En algunos casos también identifica el protocolo de acceso al recurso, por ejemplo `http:`, `mailto:`, `ftp:`, etc.
## Autoridad
elemento jerárquico que identifica la autoridad de nombres (por ejemplo `//www.example.com`).
## Ruta
Información usualmente organizada en forma jerárquica, que identifica al recurso en el ámbito del esquema URI y la autoridad de nombres (e.g. `/domains/example`).
## Consulta
Información con estructura no jerárquica (usualmente pares "clave=valor") que identifica al recurso en el ámbito del esquema URI y la autoridad de nombres. El comienzo de este componente se indica mediante el carácter '?'.
## Fragmento
Permite identificar una parte del recurso principal, o vista de una representación del mismo. El comienzo de este componente se indica mediante el carácter '#'.
>El fragmento es una parte de la URI que se maneja únicamente en el lado del cliente (navegador web). Cuando el navegador recibe la respuesta del servidor y carga el recurso, el fragmento se utiliza para desplazarse directamente a la parte correspondiente del recurso en la página web.


# URL
> Una URL es un tipo específico de URI que proporciona la ubicación exacta de un recurso en la web, junto con el método para acceder a él. Una URL consta de varios componentes, como el esquema (protocolo utilizado, como "http" o "https"), el dominio (nombre del sitio web), el puerto, la ruta y, opcionalmente, parámetros y fragmentos. Ejemplo: `https://www.ejemplo.com/pagina`.

# URN
> Un URN es otro tipo de URI que se utiliza para identificar un recurso de manera única sin necesariamente indicar su ubicación o método de acceso. A diferencia de las URLs, los URNs no están vinculados a la ubicación física del recurso en la web. Ejemplo de URN: `urn:isbn:0451450523` para identificar un libro por su número ISBN.

