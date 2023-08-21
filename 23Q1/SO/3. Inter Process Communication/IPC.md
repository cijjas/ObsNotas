IPC o mejor dicho Inter Process Communication es un paradigma de funcionamiento de forma tal que los procesos sean cooperativos. Con la ventaja de poder 
- **Compartir Información**
- **Acelerar computación**
- **Modularidad** (dividir un sistema en modulos o componentes separados que hacen cosas específicas)
- **Conveniencia**

Para eso hay dos **modelos fundamentales**
1. [[Pasaje de mensajes]] (Message passing)
2. [[Memoria compartida]] (Shared memory)

![[Pasted image 20230713140752.png]]


Con los beneficios de IPC vienen algunas desventajas de mantenimiento como por ejemplo la sincronización. Muchos procesos queriendo acceder a un mismo espacio de memoria puede causar problemas (el espacio de memoria se considera una [[Región Crítica]]). Uno de estos problemas es una instancia de [[Race Condition]] 


Otro concepto propio de IPC es [[Deadlock]] 


Y algunos problemas clásicos de IPC son :
- [[Philosophers]]
- [[Readers and Writers]]

***

### [[Ejercicios IPC]]