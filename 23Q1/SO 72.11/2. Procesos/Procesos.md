Un proceso es una instancia en ejecución de un programa o una tarea. Representa una entidad activa que realiza una secuencia de instrucciones y puede interactuar con otros procesos y recursos del sistema.

El [[Sistema Operativo]] es responsable de administrar y coordinar los procesos en el sistema, asignar recursos, programar su ejecución y garantizar la ejecución segura y eficiente de los mismos. También proporciona mecanismos de comunicación y sincronización entre procesos, como IPC (Inter Process Communication), para facilitar la cooperación y la interacción entre ellos.

> Todo el software ejecutable se organiza en procesos secuenciales o simplemente procesos

- **Proceso**: [[Abstracción]] de programa en ejecución
- **Programa**: Almacenado en Disco, no hace nada

CPU = [[Procesador]]

### Conceptualmente
Un proceso tiene 
- su propio CPU
- sus propios registros
- sus propias variables
![[Pasted image 20230713132453.png]]
### Pseudo-Paralelismo
![[Pasted image 20230713131739.png]]
En una situacion de paralelismo real, habría varias CPUs compartiendo [[Memoria]].

### Creación de procesos y Terminación de procesos
La creación y terminación de procesos en [[POSIX]] recae en las funciones de [[Manejo de procesos]].

![[Pasted image 20230713133356.png]]



### Casos de creación de procesos
- **Sistemas simples** como un microondas
- **Sistemas de propósito general** compus y etc.
	- Cuando se inicial el SO
		- Daemons
	- Un proceso solicita crear otro proceso
		- Script bash y comandos UNIX
		- Formular el problema en términos de problemas relacionados
	- Un usuario solicita crear un nuevo proceso
		- Terminal,  interfaz gráfica
	- Inicio de un trabajo por lotes
		- Aplicable a mainframes, cuando hay recursos disponibles se toma el siguiente trabajo


### Jerarquía de procesos
En [[POSIX]] es una jerarquía de árbol
![[Pasted image 20230713133829.png]]
Un padre y sus descendientes forman un grupo de procesos. *Init* es la raíz del árbol.

En Win32 no existe una jerarquía de procesos
- El padre recibe un handle para manejar al proceso
- El handle se puede transferir a otro proceso

## Estados de un proceso
![[Pasted image 20230713134357.png]]

## Implementacion de procesos
-  Se mantiene una tabla de procesos
-  Cada entrada se denomina PCB (Process Control Block)
-  Información necesaria para pasar de ready a running a blocked
![[Pasted image 20230713134555.png]]


### Cuentas para saber el uso de CPU

Donde 
- $p :$ tiempo que pasa el proceso esperando por I/O (bloqueado)
- $n :$ cantidad de proceso en momoria al mismo tiempo
- $p^{n} :$ probabilidad de que los n procesos estén esperando (CPU libre)
Luego

$$
cpuUsage = 1- p^{n}
$$
![[Pasted image 20230713135501.png]]
^CPU utilization as a function of number of processes in memory

## Info sobre un proceso 
![[Pasted image 20230713134645.png]]


***

### [[Ejercicios PROCESOS]]