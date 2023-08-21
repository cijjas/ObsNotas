- Más simple en sistemas distribuidos
- Útil para pequeñas cantidades de información
- Intervención del kernel
- Operaciones
	- send(message) y receive(message)
- Es necesario un canal de comunicación (memoria, bus, red)


### Identidad
- Los procesos tienen que tener mecanismo para referirse entre sí
	- **Comunicación Directa - Simétrica**
		- `send(P, message)`, `receive(Q, message)` donde P y Q son procesos
		- Cada proceso debe conocer la identidad del otro proceso
		- El canal de comunicación se hace explícito entre un par de procesos
		- El canal de comunicación asocia exactamente a 2 procesos
		- 2 procesos pueden tener un único canal de comunicación
	- **Comunicación Directa - Asimétrica**
		-   `send(P, message)` , `receive(id, message)`
	- **Comunicación Indirecta**
		- Los mensajes se envían a puertos o casillas de correo
		- `send(A, message)` , `receive(A, message)` (A casilla de correo)
		- El canal de comunicación se establece entre procesos que comparten una casilla
		- El canal de comunicación puede asociar más de 2 procesos
		- 2 procesos pueden tener más de 1 canal de comunicación
		- Ejemplo: P1 envía mensaje a la casilla A y P2 y P3 reciben de la casilla A
			- ``` P1 : send(A, message), P2: receive(A, message), P3:receive(A, message) ```

### Sincronización
`send` y `receive` pueden ser bloqueantes o no bloqueantes
- `send` bloqueante: hasta que llega a la casilla / proceso
- `send` **no** bloqueante: resume inmediatamente
- `receive` bloqueante: hasta que hay mensaje disponible
- `receive` **no** bloqueante: recibe mensaje o null

### Buffering
Los mensajes residen en un buffer
- Capacidad 0: no buffering -> send debe bloquear
- Capacidad acotada: send debe bloquear si se agota el espacio
- Capacidad no acotada: send no bloquea

### [[Pipes]]


### [[Sockets]]
