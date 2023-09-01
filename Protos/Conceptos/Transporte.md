> Conecta dos aplicaciones

- Provee la comunicación lógica entre dos procesos que corren en distintos hosts
- Ejecutan en las «puntas finales»
	- El que envía: separa los mensajes en segmentos y los entrega al nivel de red
	- El que recibe: reensambla los segmentos en mensajes y los pasa al nivel de aplicación
- Protocolos de transporte: UDP, TCP y SCTP

![[Pasted image 20230825192841.png]]


- [[Red de Computadoras#TCP/IP]] ofrece:
	- Control de congestión
	- Control de flujo
	- Establecimiento de conexión
- UDP ofrece:
	- «mejor esfuerzo» (como IP)
- NO ofrecen:
	- Mínimo de demora o latencia
	- Mínimo de ancho de banda



# UDP

> Transporta datos de manera no confiable entre hosts. Tampoco es orientado a conexión.

![[Pasted image 20230901171312.png]]


# TCP

Semejante a UDP pero orientado a conexión.

ACK reconoce cuantos bytes recibió.