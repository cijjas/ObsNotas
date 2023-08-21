Un i-node, también conocido como nodo-i o nodo de indexación, es una estructura de datos utilizada en sistemas de archivos para almacenar metadatos asociados con un archivo en particular. Cada archivo en un sistema de archivos Unix-like, utiliza un i-node para describir sus propiedades y ubicación física en el almacenamiento.
![[Pasted image 20230714095245.png]]
Se reserva la última posición para un bloque con más direcciones.

## Atributos
1. Número de i-node: Es un identificador único asignado a cada i-node y se utiliza para referenciar el archivo.
2. Permisos y atributos: Almacena los permisos de acceso del archivo, como lectura, escritura y ejecución, así como otros atributos, como propietario, grupo, fechas de creación y modificación.
3. Tamaño del archivo: Indica el tamaño del archivo en bytes.
4. **Punteros a bloques de datos**: Los i-nodes generalmente almacenan punteros a bloques de datos que contienen el contenido real del archivo. Estos bloques pueden ser directos, indirectos o doblemente indirectos, dependiendo del tamaño del archivo.
5. Información de timestamps: Registra las fechas y horas asociadas con el archivo, como la última modificación, acceso y cambio de metadatos.
6. Enlaces: Indica el número de enlaces duros (hard links) que apuntan al mismo i-node. Los enlaces duros son múltiples entradas de directorio que apuntan al mismo archivo.
7. Otros metadatos: Puede incluir información adicional como el tipo de archivo, atributos extendidos, número de bloque de dispositivo (para archivos especiales), entre otros.

## Propósito
El i-node proporciona una forma eficiente de acceder y administrar los atributos y ubicación del archivo en el sistema de archivos. Al utilizar una estructura de datos de i-node, el sistema de archivos puede localizar rápidamente la información necesaria para un archivo sin tener que buscar en todo el sistema de archivos.