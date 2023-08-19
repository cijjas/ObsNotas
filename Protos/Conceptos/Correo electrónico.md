Previo a internet

> En un sistema Unix/Linux, toda cuenta de usuario tiene también una cuenta de mail.

![[Pasted image 20230818193914.png]]

# SMTP

> El protocolo por el cual se transmiten los mails por Internet es SMTP (Simple Mail Transport Protocol), definido en RFC821(1982) y RFC5321(2008).

![[Pasted image 20230818194824.png]]

- Usa TCP para transferir mensajes desde el cliente al servidor (puerto 25)
- Transferencia directa: desde "sending server" a "receiving server"
- Tres fases
	- handshaking
	- transferencia de mensajes
	- cierre
- Interacción comando / respuesta
	- comando: texto ASCII
	- respuesta: código de status y comentario
- Los mensajes son US-ASCII: ASCII-7 bits
