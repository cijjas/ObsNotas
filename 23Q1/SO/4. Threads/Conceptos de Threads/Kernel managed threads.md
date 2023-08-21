
![[Pasted image 20230713194254.png]]
- No es necesario el run-time system ni tabla de threads (en espacio de usuario)
- Un thread se bloquea como es usual y el kernel elige otro thread (u otro proceso)
- Debido al mayor costo, se pueden reutilizar los threads