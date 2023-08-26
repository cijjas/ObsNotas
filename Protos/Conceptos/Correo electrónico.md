
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


# POP3
> Protocolo para recibir mails
![[Pasted image 20230825172415.png]]


En realidad cuando yo abro un mail en gmail, el protocolo por el cual leo el mail es [[HTTP]] que por detrás mi computadora optuvo o envío mediante [[#SMTP]] o [[#POP3]]

## POP 3 comandos
![[Pasted image 20230825172931.png]]


# Webmail
> Es un cliente de correo electrónico (MUA) con una interface web, que permite acceder al mailbox de un usuario. (basicamente gmail o fibertel y sus interfaces),


# IMAP
> Te deja ver el mail sin descargarlo

## IMAP comandos
![[Pasted image 20230825173150.png]]


# Formato del mensaje

- Una envoltura primitiva (ver RFC 821).
-  Campos de cabecera (From: .., To: ..., etc.) (los usuarios pueden definir cabeceras que comiencen con X)
-  Una línea en blanco
-  Cuerpo del mensaje

> El E-mail es probablemente la aplicación TCP/IP más usada. Sin embargo, SMTP y RFC 822 se limitan a texto ASCII de 7 bits con una longitud de línea máxima de 100 caracteres. Por esto se recurre a [[#Base64]]


# Base64
- Método de codificación simple
- Cada grupo de 3 bytes es codificado como 4 bytes, cada uno conteniendo sólo 6 bits de datos
- Estos son enviados como “7-bit ASCII”
- Base64
	- 6 bits  -> [0,63]
	- Se asigna un carácter a cada número

![[Pasted image 20230825173641.png]]

Si la cantidad de bits no es múltiplo de 6, **Se agregan ceros al final hasta un múltiplo de 6.**
- Uno o dos caracteres de relleno (‘=‘) son agregados para que sea múltiplo de 6 bytes.
- En general se agrega un solo carácter de relleno
![[Pasted image 20230825173933.png]]

[Base64 DOC](https://www.base64encode.net)

# [[MIME#SMTP no puede transmitir objetos binarios.]]
