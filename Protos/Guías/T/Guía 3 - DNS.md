
[Guía 3](https://docs.google.com/document/d/1KS1umi5imW8Yg71VxjeQBKzLT3_GdbqTfqwrhPxgfdQ/edit)
[SMTP ejemplo](https://docs.google.com/document/d/1ZqTQHk5ccXPu_PK2T08OaJJQBZG6UVeK6rve5oOQ274/edit)
[[DNS]] y [[Correo electrónico]]

# 1
> Desde mi notebook y situado fuera del ITBA, puedo establecer una sesión SSH a “pampero.itba.edu.ar”, pero estando dentro del ITBA no. Mis servidores DNS fijos son de los de Google: 4.4.4.4 y 8.8.8.8. ¿Por qué falla y cómo se resuelve?

Lo que pasa es que al tener los servidores DNS fijos de google, cuando estás adentro del ITBA va a pensar que te estás intentando conectar desde afuera estando adentro. Es como que un ciudadano vaya a preguntarle al indec del 2013 los verdaderos datos de la pobreza argentina.

## Split Horizon
El "split horizon" es una estrategia utilizada en redes y servidores DNS (Domain Name System) para evitar problemas de comunicación. Funciona así:
1. **Cuando estás dentro de un lugar (como una red o institución):** Los servidores DNS te dan direcciones que funcionan dentro de ese lugar. Es como un mapa detallado para moverte dentro de esa zona. Esto puede ser útil para acceder a servicios locales y mantener el tráfico dentro de la red.
2. **Cuando estás fuera de ese lugar:** Los servidores DNS te dan direcciones que funcionan desde fuera. Es como otro mapa que te guía desde lugares externos. Esto es importante para que puedas acceder a los mismos servicios, pero de manera segura desde cualquier parte.

# 2

> Un servidor DNS debe escuchar peticiones tanto UDP como TCP, por lo que un cliente DNS puede elegir utilizar cualquiera de ellos como protocolo de transporte. Nombrar un caso en el cual sea mejor usar UDP y un caso en el cual sea preferible usar TCP

Conviene UDP si la rta es corta y entra en un datagrama (el encabezado TCP ocupa más bytes que UDP y con UDP no es necesario intercambiar paquetes para iniciar y luego cerrar la conexión). Si supiéramos que la rta es extensa y necesita varios datagramas, sería más sencillo iniciar el pedido usando TCP
## UDP
No orientado a conexión ni confiable
### Ventaja
Más rápido, menor overhead. Es como mandar datos sin esperar una respuesta. Un caso ejemplo es el de transmisión de video.

## TCP
Orientado a conexión y confiable.

### Ventaja
ejemplos: email, web browsing, software updates, y la mayoría de cosas no triviales.

> TCP is better suited for situations where data integrity, accuracy, and reliable communication are top priorities.


# 3
> Se consulta vía UDP a un servidor DNS, pero la respuesta no entra en un datagrama, ¿cómo se resuelve? ¿Lo debe contemplar el protocolo de transporte o el de aplicación?

**CHUNKIN'.**

# 4

> Un programa de correo (Thunderbird, app de mail para celular, etc.) sólo nos pregunta cuenta de correo y contraseña,
> - ¿Cómo sabe cuál es el servidor al cual tiene que conectarse para enviar un mail? 
> - ¿Por qué puede ser que falle la conexión al servidor de mail? (descartar cosas como contraseña inválida, falta de señal, no hay internet, etc.)

- Sabe cuál es el servidor consultando el regristro MX para el dominio al cual pertenece el mail. 
- Más allá de la respuesta obvia (mal configurada la zona), el servidor DNS sólo informa la IP del MX, si no escucha en el puerto estándar fallará la conexión.

# 5
> El IP de un FQDN ha cambiado, el servidor DNS que utilizo ya conoce la nueva IP, sin embargo en mi computadora me lo sigue resolviendo con la vieja IP. Nombrar dos razones por las que puede estar sucediendo esto y cómo resolverlo

La razón es que el TTL aún no ha precedido y entonces no se actualiza la cache. También puede ser que este hardcodeado en /etc/hosts.

# 6

> El IP de un servidor HTTP ha cambiado, pero mi servidor DNS lo sigue resolviendo con la vieja IP.
> - Si yo conozco la nueva IP, ¿puedo usarla directamente en el browser en vez del FQDN? ¿Funciona siempre, nunca o a veces?
> - ¿Cómo puedo hacer para conectarme al servidor web por nombre -sabiendo la nueva IP- sin esperar que lo resuelva correctamente mi servidor DNS?
> - Si no conozco la nueva IP, ¿qué puedo hacer para averiguarla?

- Depende: a veces, ya que la URL (en este caso el IP) irá en la directiva “Host” del header de HTTP.
- Agregando el ip a /etc/hosts
- Si, con dig o hosts o 


# 7
``dig +short . NS`
![[Pasted image 20230821134407.png]]$\ldots$


# 8
1. SMTP: orientado a conexión, confiable
2. POP3: orientado a conexión, confiable
3. DNS: no orientado a conexión, no confiable (sin importar si usa TCP o UDP)

# 9
> Analizar la veracidad de las siguientes afirmaciones:
> - SMTP usa TCP como protocolo de transporte, eso garantiza que el mail que yo envío será recibido por el destinatario final.
> - Yo uso Gmail desde un browser. Eso quiere decir que en el envío de mis mails no interviene SMTP.
> - El uso de IMAP ha perdido popularidad desde que existe Gmail y otros webmails.

- Falso. Sólo garantiza que sabré con certeza si llega o no hasta mi servidor SMTP.
- Falso, Para enviarlo al servidor de mails del destinatario debe usar SMTP (salvo que sea otro usuario de Gmail cuya cuenta esté alojada en el mismo servidor que el mío)
- es verdad. IMAP se usa principalmente por dos razones:
	1. para cuentas compartidas, como por ejemplo la cuenta de información o soporte de una empresa, ya que permite que una persona marque el mail como leído, lo mueva a otra carpeta, etc y además todos los que acceden pueden ver si se leyó, se envió una respuesta, etc.
	2. Dejar los mails en el servidor, sabiendo cuál está leído y cuál no. Al bajarlos (usando POP) a una computadora corremos el riesgo de que se pierdan todos los mails, y que sin tener esa computadora no se pueden leer los mails viejos.
# 10
> ¿Por qué tomarse la molestia de usar Split-horizon al configurar un servidor DNS? ¿Por qué no asociar el nombre del host únicamente a la IP pública?

Una ventaja es que el host que esté dentro de la red local podrá enviar paquetes IP directamente al host destino, sin necesidad de la intervención de un router/firewall. Además, si se usa el mismo dominio en forma privada que en forma pública, permite establecer que algunos nombres de hosts (y su IP privada) no sean visibles por queries realizadas fuera de la organización, y cuanto menos información pública exista, menos riesgos de vulnerabilidad habrá.

