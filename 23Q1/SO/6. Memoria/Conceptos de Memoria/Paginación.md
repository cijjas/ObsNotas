Técnica de gestión de memoria utilizada en sistemas operativos y sistemas de memoria virtual para organizar y administrar la [[Memoria|Memoria]] de manera eficiente. En la paginación, la memoria física y la memoria virtual se dividen en bloques de tamaño fijo llamados "páginas".

Cada página tiene un tamaño uniforme y se utiliza para almacenar secciones contiguas de memoria lógica o virtual. Por otro lado, la memoria lógica o virtual se divide en bloques del mismo tamaño llamados "marcos de página".

La tabla de páginas (page table) mapea las páginas virtuales a los marcos de página físicos correspondientes. Cuando un programa o proceso accede a una dirección de memoria virtual, el sistema operativo utiliza la tabla de páginas para determinar la correspondiente dirección de memoria física.


![[Pasted image 20230713224957.png]]


![[Pasted image 20230713225016.png]]


## Tabla de páginas
Tabla con muchas de estas entradas
![[Pasted image 20230713225158.png]]
![[Pasted image 20230713225223.png]]
![[Pasted image 20230713225305.png]]

## TLB (Translation Lookaside Buffers)

La TLB (Translation Lookaside Buffer) es una memoria caché especializada (generalmente adentro de la [[Memoria Virtual#MMU (Memory Management Unit)]]) utilizada en los sistemas de memoria virtual para mejorar la velocidad de las traducciones de direcciones virtuales a direcciones físicas. (Cache de traducción)


## Si EDV es muy grande
Dos enfoques
### Tabla de páginas multinivel
![[Pasted image 20230713225946.png]]

![[Pasted image 20230713230005.png]]


### Tabla de páginas invertidas
  
En este esquema hay una entrada por cada PF en lugar de cada VP
![[Pasted image 20230713230051.png]]
![[Pasted image 20230713230106.png]]



## [[Algoritmos de Reemplazo de Páginas]]
