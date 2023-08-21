Refiere al proceso mediante el cual un sistema operativo o un administrador de tareas decide el orden en que se ejecutan los procesos o hilos de un sistema computacional. Es la forma en que se asigna y se comparte eficientemente el tiempo de CPU entre los diferentes [[Procesos]] y tareas en un [[Sistema Operativo]].

## Objetivo
Maximizar la utilización de los recursos del sistema

## Comportamiento de un Proceso
- Usualmente los procesos alternan entre uso de CPU e I/O
- Nomenclatura: I/O => bloquearse esperando por un evento. Por ejemplo, escribir la memoria devideo para refrescar la pantalla se considera uso de CPU.
- CPU-bound vs I/O-bound (la clave es la longitud de la ráfaga de CPU, no de I/O)
- Con procesadores más rápidos los procesos se vuelven más I/O-bound

![[Pasted image 20230713195554.png]]


## Clasificación
Preemptive $\approx$ (Interrumpible)
- **Non-preemptive** : elige un proceso hasta que este libera el CPU voluntariamente o que termine
- **Preemptive** : Elige un proces y corre hasta que se vence el plazo establecido ([[Quantum]]). Para esto es necesario la interrupción del timer.
***

## Paradigmas de Scheduling
Las decisiones de scheduling para diferentes tipos de sistemas operativos puede variar.

Algunos sistemas de scheduling:
#### All systems
	- Objetivos
		- Fairness - giving each process a fair share of CPU
		- Policy enforcement - seeing that stated policy is carried out
		- Balance - keeping all parts busy
#### Batch systems
	- No hay interaccion con el usuario
	- Non-preemptive o preemptive con quantum largo
	- Objetivos
		- Throughput - maximize jobs per hour
		- Turnaround time - minimize time between submission and termination
		- CPU utilization - keep CPU busy all the time
#### Interactive systems
	- Preemptive
	- Uso general
	- Objetivos:
		- Response time - respond to requests quickly
		- Proportionality - meet users expectations
#### Real-time systems
	- Sorpresivamente a veces no es necesario un scheduler preemptive
	- Uso específico, programas específicos
	- Objetivos
		- Meeting deadlines - avoid loosing data
		- Predictability - avoid quality degradation in multimedia systems

***

## Algoritmos de Scheduling

### Algoritmos de [[Scheduling#Batch systems]]
#### First come, first served
- Cola tradicional
- Non-preemptive
- Bloqueados van al final
- Simple y fácil de programar
- Desventaja : I/O puede tomar el control y no soltar hasta que se termino I/O

#### Shortest Job First
- Asume que los tiempos de ejecución son conocidos
- Non-preemptive
![[Pasted image 20230713205110.png]]
 * $TurnaroundTime_{(a)} = \frac{(A+(A+B)+(A+B+C)+(A+B+C+D))}{4} = 14s$
 * $TurnaroundTime_{(b)} = \frac{(B+(B+C)+(B+C+D)+(B+C+D+A))}{4} = 11s$

#### Shortest Remaining Time Next
- Versión preemptive de shortest job first
- Asume que los tiempos de ejecución son conocidos
- Al llegar un nuevo trabajo se compara su tiempo restante (total) con el restante del trabajo actual
- Beneficia

### Algoritmos de [[Scheduling#Interactive systems]]
#### Round Robin
- Preemptive
- Cada proceso adquiere un quantum para correr
	- Si al finalizar sigue ready, se le quita el CPU de todos modos
	- Si se bloquea antes de que venza el quantum, se pasa al siquiente
- Fácil de implementar
	- Lista de procesos Ready
- El tamaño del quantum es importante

![[Pasted image 20230713210555.png]]
Mientras más se acerque el [[Quantum]] al tiempo de context switch, más es el tiempo perdido.

#### Priority Scheduling
- Round-Robin asume que todos son igual de importantes
- Se le asignan prioridades a los procesos y aquellos con la máxima prioridad son elegidos
- Preemptive
- La prioridad puede asignarse estática o dinámicamente
	- Dependiendo del usuario
	- Dependiendo del comportamiento del proceso
		- Para I/O-boun puede ser 1/f donde f es la proporción del último quantum usado

#### Priority Scheduling with Multiple Queues
![[Pasted image 20230713211103.png]]

#### Priority Scheduling - Shortest Process Next
![[Pasted image 20230713211217.png]]
#### Guaranteed Scheduling
- Prometamos que si hay n usuarios conectados, cada uno recibirá 1/n del tiempo de CPU
- Alternativamente, si 1 usuario tiene n procesos, cada proceso recibirá 1/n del tiempo de CPU
- Registrar el tiempo de uso de cada usuario / proceso en términos de la proporción usada
- Elegir aquel proceso con el la menor proporción

#### Lottery Scheduling
- Cada proceso tiene tickets de “lotería” para diferentes recursos.
- ¡Vamos a sortear 20ms de CPU 50 veces por segundo (50Hz)!
- ¿Y si asignamos más tickets a algunos procesos? -> poseer una fracción f de los tickets implicaobtener una fracción f del recurso
- Procesos que cooperan entre sí pueden compartir tickets
- Resolver problemas complejos con otro algoritmo: servidor de video que provee de stremming asus clientes con diferentes frame rates -> 10, 20 y 50 FPS

#### Fair-Share Scheduling
![[Pasted image 20230713211505.png]]


*** 
### [[Ejercicios SCHEDULING]]
