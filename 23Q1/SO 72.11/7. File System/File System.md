Un file system o sistema de archivos es una estructura de datos ([[Abstracción]] :: Los archivos son una abstracción del disco, de hecho, se pueden ver como un espacio dedirecciónes) utilizada por los sistemas operativos para organizar, almacenar y recuperar archivos en medios de almacenamiento, como [[Disco]], unidades USB, tarjetas de memoria, entre otros.

El sistema de archivos proporciona una forma estándar y eficiente de gestionar archivos y directorios en el almacenamiento. Define la forma en que los archivos se organizan, se nombran, se almacenan y se acceden.

El file System se encarga de 
 - Estructurados
 - Nombrados
 - Accedidos
 - Usados
 - Protegidos
 - Implementados
 - Administrados

Queremos resolver 3 problemas
- Almacenar mucha información, que quizás no entra en el EDV
- Persistencia luego de la muerte del proceso
- Múltiples procesos accediendo a la misma información


MBR : Master Boot Record que carga el bootblock de la partición activa
Cada partición tiene su Boot block y su Superblock

![[Pasted image 20230714093154.png]]


## Asignación contínua
Los archivos se almacenan uno al lado del otro en disco
#### Ventajas
- Fácil de implementar
- Excelente rendimiento de disco (secuencial y random)

#### Desventajas
- [[Fragmentación#Fragmentación Externa]]
- Conocer el tamaño a priori

![[Pasted image 20230714093942.png]]


## Asignación con Listas Enlazadas en [[Disco]]
![[Pasted image 20230714094105.png]]
- La primer palabra de cada bloque es un puntero al siguiente bloque
- Solo necesitamos el puntero al primer bloque

## Asignación con Listas Enlazadas en [[Memoria|Memoria]]
El concepto es el mismo pero la tabla se almacena en memoria. Se conoce como FAT (File Allocation System).
![[Pasted image 20230714094836.png]]

## i-nodes
Cada File tiene un [[i-node]]


## Directorios
![[Pasted image 20230714095411.png]]

## Archivos Compartidos
![[Pasted image 20230714095748.png]]
### 2 enfoques
- Hard link: Existe 1 único i-node para estearchivo y es apuntado por ambosdirectorios
- Symbolic Link: Crear un archivo de tipo LINKen el directorio de B con la rutareal del archivo
![[Pasted image 20230714095720.png]]


## Log-Structured File System (LFS)

![[Pasted image 20230714095842.png]]
![[Pasted image 20230714095900.png]]

## Journaling File System (JFS)
![[Pasted image 20230714095930.png]]
![[Pasted image 20230714095941.png]]




***
### [[Ejercicios FILE SYSTEM]]
