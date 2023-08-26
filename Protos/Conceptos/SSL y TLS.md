# Secure Sockets Layer
> Para encriptar datos desde y hacia el servidor, un Web Server puede usar SSL (Secure Sockets Layer).


- Una capa intermedia entre protocolos de aplicación y de transporte (TCP). Por ejemplo entre [[HTTP]] y  [[Correo electrónico#SMTP]] 
- Permite a un servidor que "hable" SSL autenticarse a sí mismo con un cliente que "hable" SSL
- Permite a un cliente autenticarse con un servidor
- Permite encriptar la conversación entre cliente y servidor


ITCROWD

![[Pasted image 20230825184202.png]]

# Clave simétrica
![[Pasted image 20230825184222.png]]

# Clave Pública y Clave Privada
![[Pasted image 20230825184255.png]]
- ¿Como confío en la clave pública? : [[#Métodos de seguridad]] y [[#Certificados]]

# Clave Privada y Clave Pública 
![[Pasted image 20230825184640.png]]



# Métodos de seguridad

![[Pasted image 20230825184932.png]]

![[Pasted image 20230825185034.png]]

![[Pasted image 20230825185054.png]]



## Ejemplo de conexión segura
![[Pasted image 20230825190819.png]]
> Generalmente solo se usa clave publica y privada para generar las claves siétricas internamente ya que el método PP (clave públic ...) es pesado


# Certificados
![[Pasted image 20230825185215.png]]
![[Pasted image 20230825190533.png]]






# TLS

# Transport Layer Security
- Conexión segura por puerto: 443 para "https", 993 para "IMAPs", 995 para "POPs", etc. Usa SSL
- Conexión segura por protocolo: comienza con un "hello" inseguro y luego cambia a una conexión segura. Ejemplo: comando STARTTLS en SMTP
- TSL y SSL proprocionan el mismo nivel de encriptación. Difieren en cómo se inicia la conexión segura.
