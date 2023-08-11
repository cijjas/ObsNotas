La memoria virtual es una técnica utilizada en los sistemas operativos para ampliar la capacidad de almacenamiento de un sistema más allá de la memoria física disponible. Proporciona una ilusión de que el sistema dispone de más memoria de la que realmente tiene, permitiendo ejecutar programas más grandes y manejar múltiples procesos simultáneamente.

## Ventajas
1. Mayor capacidad: Permite ejecutar programas que superan la cantidad de memoria física disponible, ya que se pueden cargar y descargar páginas según sea necesario.
2. Protección de memoria: Cada proceso tiene su propio espacio de direcciones virtuales, lo que brinda protección y aislamiento entre procesos. Un proceso no puede acceder directamente a la memoria de otro proceso.
3. Compartición de memoria: Varios procesos pueden compartir páginas de memoria, lo que ahorra recursos y permite una comunicación más eficiente entre ellos.
4. Menor fragmentación: Al utilizar técnicas de paginación o segmentación, se puede reducir la fragmentación de memoria y aprovechar de manera más eficiente el espacio disponible.

## MMU (Memory Management Unit)
- Cada proceso tiene su espacio de direcciones
- Este espacio está dividido en bloques llamados **páginas**
- Cada página es un conjunto contiguo de direcciones

![[Pasted image 20230713224827.png]]


Esto nos lleva obviamente a [[Paginación]]