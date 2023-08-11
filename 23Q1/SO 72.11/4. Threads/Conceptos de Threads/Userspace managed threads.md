
![[Pasted image 20230713193323.png]]

#### Userspace
![[Pasted image 20230713193706.png]]
- Cada proceso necesita su tabla de threads privada -> análoga a la tabla de procesos del kernel
- Si un thread se bloquea localmente (esperando por otro thread del mismo proceso) se realiza el switch en espacio de usuario
	- Es un orden (o más) de magnitud más rápido que el switch usual con interrupciones y laintervención del kernel.
	- No es necesario flushear la cache
- Cada proceso puede tener su propio algoritmo de scheduling de threads

Esta implementación viene con desventajas 
![[Pasted image 20230713193903.png]]