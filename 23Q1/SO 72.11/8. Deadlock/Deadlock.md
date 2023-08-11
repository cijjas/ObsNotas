Un conjunto de procesos está bloqueado (en estado de deadlock) si cada proceso del conjunto está esperando un evento que solo puede causar otro proceso del conjunto.

## Preemptable and Non-preemptable Resources
- Recurso : Cualquier cosa que pueda ser adquirida, usada y liberada
- Preemtable resource : Se le puede quitar a un proceso sin causar problemas
- Non-preemtable resource : No se le puede quitar a un proceso sin causar problemas
![[Pasted image 20230714101404.png]]

## Condiciones de Coffman
Necesarias no suficientes.
1. Exclusión mutua (Mutual Exclusion): Al menos un recurso debe ser asignado exclusivamente a un proceso en un momento dado, lo que significa que no puede ser compartido simultáneamente por múltiples procesos.
2. Espera en retención (Hold and Wait): Un proceso debe estar reteniendo al menos un recurso mientras espera para obtener otro recurso adicional que está siendo utilizado por otro proceso. Esto puede llevar a situaciones en las que los procesos se mantengan esperando indefinidamente mientras retienen los recursos existentes.
3. No apropiación o no prelación (No Preemption): Los recursos asignados a un proceso no pueden ser forzosamente liberados o "arrebatados" por el sistema. Solo el proceso que mantiene un recurso puede decidir cuándo liberarlo voluntariamente.
4. Espera circular (Circular Wait): Existe una cadena circular de dos o más procesos, donde cada proceso en la cadena está esperando un recurso que está siendo retenido por el siguiente proceso en la cadena. Esto crea una situación de espera mutua cíclica, en la que ningún proceso puede avanzar porque está esperando que se libere un recurso controlado por otro proceso en la cadena.

## Modelado de Deadlock
- Cuadrado: Recursos
- Circunferencia: [[Procesos]]
![[Pasted image 20230714101618.png]]

## Prevención de Deadlock
1. Ignorar el problema
2. Detection and recovery. Let them occur detect them and take action
	1. Detección con 1 recurso de cada tipo
		1. Construimos el grafo de asignación de recursos
		2. Si no existen ciclos $\rightarrow$ no hay deadlock
		3. Existen algoritmos simples para detectar ciclos en grafos
	2. Detección con múltiples recursos de cada tipo
		1. ![[Pasted image 20230714102552.png]]
			1. Look for unmarked process $P_i$, for which the i-th row of R is less than or equal to A
			2. If such process is found, add the i-th row of C to A, mark the process and go back to 1.
			3. If no such process exists, terminate.
		2. ![[Pasted image 20230714102757.png]]
	3. Recuperación de Deadlock
		1. Quitar el recurso (preempt). Que sea transparente para el proceso. Usualmente difícil sinoimposible
		2. Rollback mediante el uso de checkpoints.
		3. Matar uno de los procesos involucrados, o uno que tenga un recurso solicitado por algún procesoen estado de deadlock
3. Dynamic avoidance by careful resource allocation.
	1. ![[Pasted image 20230714102935.png]]
	2. Estados seguros e inseguros
		1. ![[Pasted image 20230714103016.png]]
	3. Algoritmo del banquero
		1. ![[Pasted image 20230714103051.png]]
		2. ![[Pasted image 20230714103112.png]]
4. Prevention, by structurally negating one of the four conditions.
	1. ![[Pasted image 20230714103148.png]]


## Ejemplos de Deadlock 
![[Pasted image 20230714101422.png]]

![[Pasted image 20230714102013.png]]

```c
semaphore mutex = 1;
void foo(){
	down(mutex);
	down(mutex);
}
```

```c
semaphore mutexA = 1;
semaphore mutexB = 1;
void P1(){
	down(mutexA);
	down(mutexB);
}

void P2(){
	down(mutexB);
	down(mutexA);
}
```


## Deadlock de Comunicación
Supongamos que el proceso A envía un mensaje al proceso B, el cual espera hasta que llegue elmensaje. Si el mensaje se pierde, B esperará por siempre y posiblemente A también si espera unarespuesta de B.

En este escenario ningún proceso posee recursos y no se resuelve ejecutando secuencialmente A y B.No se puede Ordenando recursos (no los hay) ni planificando cuidadosamente (no se puede posponeruna solicitud)

Esto se conoce como deadlock de comunicación y es un problema de la sincronización de lacooperación

Se pueden utilizar timeouts para evitar esperas infinitas y se requiere un protocolo adecuado paraevitar más problemas

## Livelock
![[Pasted image 20230714103332.png]]


***
### [[Ejercicios DEADLOCK]]