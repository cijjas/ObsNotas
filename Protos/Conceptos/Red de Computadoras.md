Un conjunto interconectado de **hosts**. Cada host es un equipo autónomo.
# Host 
un Host puede ser cualquier cosa incluyendo computadoras
## Como envía el host
1. Toma datos de la app
2. Divide la info en paquetes de L bits de longitud
3. Transmite el paquete a la red a una tasa de transmisión  R (ancho de banda)

> Toma $\frac{L}{R}$ transmitir un paquete de $L$ bits a $R$ bps (bytes por segundo) 

### Packet Switching
![[Pasted image 20230804172927.png]]
Si la tasa del link de entrada es superior a la de transmisión en un determinado período
- Se encolan los paquetes
- Si el buffer está lleno, se *droppean* paquetes (el sender debería reenviarlo)
Por esto último hay casos en los que tener mas bps no es necesariamente mejor

# Modelos de Capas
Fue necesario definir estándares de comunicación entre computadoras, ,para lo cual se definio un modelo de capas que identifica niveles de comunicacipon

### Modelo OSI (1984)
Modelo de 7 capas
![[Pasted image 20230804173408.png]]
- Protocolo de Aplicacion : por ejemplo [[HTTP]]
- No se utilizan: 
	- Protocolo de Presentacion : "Es como un traductor"
	- Protocolo de Sesión : crea origen destino

# Protocolos
Entre cada capa hay un protocolo.
> Sistema formal de reglas de comunicación

Se pueden clasificar según el servicio que **ofrecen a su nivel superior**
- Orientados a conexión vs **NO** orientados a conexión
- Confiable vs **NO** confiable (No me entero si llegó o no (un evento en vivo))


| Orientados a conexión | NO orientados a conexión |
| ----------| ---------|
| 1. Establecer conexión | 4. Envíar información al destinatario
| 2. Intercambiar conexión | -|
| 3. Cerrar conexión |-|

|Confiable| No Confiable|
|---|---|
| 1. Confirma si la información fue recibida | 5. No asegura si recibió o no|
| 2. Utiliza acuse de recibo|-|
| 3. Reenvía informacíon de ser necesario| -| 
| 4. Informa al nivel superior si no se pudo envíar| -|

![[Pasted image 20230804175857.png]]


# TCP/IP
Sacaron capas. En su momento no eran necesarias pero despues tuvo sentido tenerlas de vuelta.

TCP es un binario.

![[Pasted image 20230804180610.png]]

# Encapsulamiento
Cuando se manda un E-Mail por ejemplo, se mandan varios bytes más que el de sus datos.
![[Pasted image 20230804181431.png]]


# Medio de comunicación Broadcast
## Targeted
En un medio de comunicación broadcast, como el ejemplo del sistema de parlantes en un supermercado, la información se coloca en el medio y puede ser recibida por todos los dispositivos conectados a ese medio. Sin embargo, la información transmitida puede estar dirigida específicamente a un único destinatario, y los demás dispositivos simplemente la ignorarán si no les concierne.
# Comunicación Broadcast
## Not targeted
Una comunicación broadcast en redes informáticas se refiere al envío de datos a todos los dispositivos en la red sin considerar la dirección de destino. A diferencia del medio de comunicación, una comunicación broadcast es enviada a todos los receptores y varios pueden usar esa info.

# LAN
## Topología del Bus
![[Pasted image 20230804185648.png]]
- Todos los hosts en la misma línea, conectados a un hub
- Cada host puede ver lo que se está transmitiendo
- Gran posibilidad de colisiones 
- Si la red crece, se la divide en segmentos (dominios de colisión)
![[Pasted image 20230804185104.png]]
## Topología de Estrella
![[Pasted image 20230804185716.png]]
- Cada host se conecta a un **switch**.
- Cada host puede ver lo que envía, recibe, o mensajes broadcast
- Dirige los datos por el puerto al que está conectado el host, pudiendo encolar distintas tramas (**frames**).
- Se basan en el número de placa (**MAC address**)
![[Pasted image 20230804185807.png]]

# NETCAT / WIRESHARK
- Wireshark levanta toda la data
- Open-source
- Con permisos de admin, coloca a la interface en modo "promiscuo"
- Permite capturar y analizar Todas las tramas que pasen por la interface
# Router
![[Pasted image 20230804191601.png]]
- Toma decisiones en base a direcciones de red y no MAC 
- Puede conectar distintas tecnologías (Ethernet, TR, WiFi)
- Separa una red en uno o más segmentos.
- Backbone de Internet, ejecutando protocolo IP
	- Establece rutas entre hosts
	- Regula el tráfico