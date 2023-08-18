
DNS es un sistema jerárquico distribuido para traducir nombres de hosts a direcciones IP. 


> Algunos nombres de dominio a resolver se pueden encontrar en /etc/hosts, pero en la mayoría de los casos deberán ser resueltos preguntando a un servidor DNS.

- Es una base de datos distribuida implementada en una jerarquía de servidores de nombre.
- Protocolo de aplicación que permita consultar dicha base.

# Cómo se ve
La información en DNS puede ser vista como un árbol invertido donde la raíz hace referencia a servidores de nombres raíz (root name servers).

![[Pasted image 20230818173803.png]]
- siempre terminan con un punto.


# Root Name Server
- Son los que conocen los [[#TLD Servidores autorizados]]
- ![[Pasted image 20230818175222.png]]
- ![[Pasted image 20230818182025.png]]

# TLD Servidores autorizados

**top-level domain (TLD) servers:**
- responsables de com, org, net, edu, aero, jobs, museums, y todos los países (ar, uk, uy, tv, etc.)
- Verisign para .com TLD, Educause para .edu TLD
**authoritative DNS servers: **
- Cada organización mantiene su propio servidor(es) DNS
- Puede ser mantenido por la misma organización o un proveedor

# Servidor DNS local
- ISP por defecto usa "default name server"
- Cuando un host realiza una consulta DNS, se fija en el cache y luego en el servidor local. Si no tiene la información busca y luego guarda en la cache.

# Búsqueda

![[Pasted image 20230818181108.png]]
- En cada búsqueda se guarda en la cache los distintos niveles, cualquier .edu.ar ya va aser más fácil buscarlo. Obvio que el tiempo se recibe en la respuesta y suele durar bastante ya que no suele cambiar la dirección.

## DNS: cache
- Una vez que el servidor de nombres aprende el mapeo, lo almacena en cache
- Expiran tras un tiempo (TTL)
- Servidores de nombre generalmente cachean la dirección de los servidores TLD
- Los Root Servers no suelen visitarse

# Configuración de un servidor DNS
- Resolver only system
- [[#Caching-only Server]]
- [[#Master servers]]
- [[#Slave servers]]

## Caching-only Server
![[Pasted image 20230818182235.png]]

## Master servers
- Es la fuente autorizada para toda la información de una zona específica.
-  Lee la información sobre el dominio desde un archivo construido por el administrador.
-  Es un server autorizado para un dominio o parte de un dominio pues puede responder con autoridad preguntas sobre ese dominio.
## Slave servers
 - Transfiere información completa de una zona desde un master server y la almacena en un archivo en el disco local.
- Mantiene información completa y actualizada de una zona y puede responder preguntas sobre zona en forma autorizada.

# Registros DNS
![[Pasted image 20230818182423.png]]
![[Pasted image 20230818182513.png]]
![[Pasted image 20230818182528.png]]

# Understanding DNS
![[understanding-dns-anatomy-of-a-bind-zone-file.pdf]]


# Utilidades
![[Pasted image 20230818190458.png]]

# DNS dinámico
![[Pasted image 20230818191430.png]]



# Spoofing
> Es el arte de lograr que un registro DNS apunte a un IP que no sea el que debería apuntar.

![[Pasted image 20230818191901.png]]
![[Pasted image 20230818192009.png]]
## Responder antes
![[Pasted image 20230818192341.png]]
- No porque usa UDP, no sirve de nada pues no es una medida de seguridad.

## Ensuciar los registros
![[Pasted image 20230818192955.png]]
