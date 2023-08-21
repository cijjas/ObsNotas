
## Óptimo
El algoritmo de reemplazo de páginas óptimo, también conocido como algoritmo de reemplazo de páginas de referencia futura, es un algoritmo teórico utilizado para evaluar el rendimiento de otros algoritmos de reemplazo de páginas en sistemas de memoria virtual.

- Reemplazar la página que se usará más lejos en el futuro
- Fácil de describir
- Imposible de implementar


### Not Recently Used (NRU)
Simple, moderadamente eficiente y rendimiento razonable aunque no óptimo
- Reemplazar la página de clase más baja
$R$ : Referenciada
$M$ : Modificada 
Clase 0: $\neg R \land \neg M$
Clase 1: $\neg R \land M$
Clase 2: $R \land \neg  M$
Clase 3: $R \land M$

Clase 1 se genera cuando hay una Clase 3 y ocurre una interrupcion del timer tick (resetea todos los bits de R) 

### First-In First-Out (FIFO)
Desalojamos la página más antigua

### Second Chance (SC)
Modificación simple de FIFO
![[Pasted image 20230713231433.png]]

### Clock (C)
Second Chance es ineficiente modificando la lista constantemente
![[Pasted image 20230713231547.png]]

### Least Recently Used (LRU)
El principio detrás del algoritmo LRU es que la página que ha sido menos recientemente utilizada es la que tiene menos probabilidad de ser utilizada en el futuro cercano. Por lo tanto, el algoritmo LRU selecciona la página que ha sido accedida menos recientemente para ser reemplazada.

Desalojar a la página que no ha sido usada el mayor tiempo
- Las páginas muy usadas recientemente suelen seguir siendo muy usadas
- Las páginas escasamente usadas recientemente suelen seguir sin ser muy usadas

2 Formas:
 - Tener una lista de páginas ordenada por tiempo de acceso. Desalojar a la más antigua
 - Tener un registro especial que cuente instrucciones y equipar a cada entrada de la tabla con espacio para este registro. Cuando se referencia una página se actualiza su contador. Desalojar a la que tenga el contador más chico

### Not Frequently Used (NFU)
1. Cada página de memoria se asocia con un contador que representa la frecuencia de acceso a esa página.
2. En intervalos regulares de tiempo, un temporizador interno o una interrupción del sistema operativo incrementa todos los contadores de las páginas en memoria.
3. Cuando se necesita reemplazar una página, se selecciona la página con el contador más bajo, lo que indica que ha sido accedida con menor frecuencia.
![[Pasted image 20230713232134.png]]

### Working Set (WS)
* En cualquier instante de tiempo t existe el conjunto de páginas referenciadas en las últimas kreferencias a memoria, este conjunto se expresa como $w(k ,t)$
![[Pasted image 20230714091932.png]]
![[Pasted image 20230713232433.png]]
Recorrer toda la tabla en cada page fault hace ineficiente elalgoritmo WS

### WSClock (WSC)
![[Pasted image 20230713232522.png]]
![[Pasted image 20230713232547.png]]


### Resumen
![[Pasted image 20230713232612.png]]