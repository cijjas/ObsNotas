
Idealmente la memoria debe ser:
- Extremadamente rápida (más rápida que la ejecución de una instrucción)
- Absurdamente grande (para meter lo que se te cante el ojete)
- Asquerosamente barata (para comprar infinitas y venderlas sobrevaloradas)
- Privada
- No volátil

### Jerarquía de memoria
![[Pasted image 20230713100836.png]]


## Sin Abstracciones
- El modelo de memoria presentado a cada proces es el de memoria física
![[Pasted image 20230713220942.png]]
![[Pasted image 20230713221029.png]]
Es visible que el `JMP 28` queda obsoleto pues esta "stackeado" y la direccion 28 ya no es lo que era antes. Por son necesarias las abstracciones ([[Abstracción]]) de memoria.

## Espacio de direcciones
El espacio de direcciones es la abstracción de la memoria.

El espacio de direcciones es el conjunto de direcciones que un proceso puede utilizar paradireccionar memoria y es independiente del de otros procesos

- Hay dos problemas principales al manejar memoria 
	1. Protección
	2. Reubicación

Lo dificil es hacer que el 28 de un proceso [[Memoria#Sin Abstracciones|Sin_Abstracciones]] de memoria sea diferente del 28 de otro proceso.

### Registros Base y Limit
Para el problema de la falta de abstracción, se crearon los registros en Hardware de **base** y **limit**
- **base** : dirección física donde se carga
- **limit** : tamaño del programa

## Memoria Física Insuficiente

Normalmente no entran todos los programas en memoria, por eso hay dos enfoques para esto:
- [[Swapping]] : guardar toda la memoria del proceso en disco y restaurarla cuando vuelva a ejecutar
- [[Memoria Virtual]] : Permitir a un proceso ejecutar incluso estando parcialmente en memoria

## Manejo de Memoria

- **Bitmap** : Se divide la memoria en bloques y cada bit representa su estado -> ¿El tamaño importa?
- **Free List** : Cada proceso y espacio libre tiene un nodo con inicio, longitud y el puntero al siguiente
![[Pasted image 20230713223457.png]]
### Ventajas y Desventajas
Ventajas del uso de un bitmap:

1. Eficiencia en el acceso: Un bitmap proporciona un acceso eficiente a los bloques de memoria disponibles o asignados. Cada bit en el bitmap representa un bloque de memoria, lo que permite una búsqueda y asignación rápidas.
    
2. Uso eficiente de memoria: El bitmap utiliza una cantidad fija de memoria para representar el estado de todos los bloques. No importa cuántos bloques haya, el tamaño del bitmap es constante, lo que lo hace eficiente en términos de uso de memoria.
    
3. Operaciones rápidas de asignación y liberación: El bitmap permite asignar y liberar bloques de memoria de manera rápida mediante operaciones lógicas de bits. Las operaciones como la asignación de un bloque pueden reducirse a una simple operación AND/OR/XOR en el bitmap.
    

Ventajas del uso de una free list (lista libre):

1. Flexibilidad en el tamaño de bloques: Una free list permite manejar bloques de memoria de diferentes tamaños. Cada elemento de la lista puede contener información sobre el tamaño y la ubicación de un bloque libre, lo que permite una asignación más precisa y específica según las necesidades del programa.
    
2. Uso eficiente del espacio: Si hay fragmentación de memoria, la free list puede organizar los bloques de memoria disponibles de manera más eficiente que un bitmap. Esto puede ayudar a reducir el desperdicio de memoria y permitir una asignación más efectiva de bloques contiguos.
    
3. Facilidad para la gestión de memoria no contigua: Si la memoria no se encuentra en una ubicación contigua, la free list puede manejarla de manera más efectiva. Cada elemento de la lista puede apuntar a un bloque de memoria independiente, permitiendo un mejor manejo de la fragmentación y la asignación.



## Algorítmos de Búsqueda de Meoria Libre
Buscar un bloque libre, luego se parte en 2, lo necesario y lo que sobra (si sobra)

### First Fit 
Comenzando desde el principio, el primer bloque suficientemente grande

### Next Fit
Comenzando desde donde quedamos, el primer bloque suficientemente grande

### Best Fit
Recorre toda la lista y elige el bloque más pequeño, pero suficientemente grande.

### Worst Fit
Recorre toda la lista y elige el bloque más grande

### Quick Fit
Previamente Ordenado por tamaño frecuentemente solicitado El primer bloque de la lista correspondiente

***

### [[Ejercicios MEMORIA]]
