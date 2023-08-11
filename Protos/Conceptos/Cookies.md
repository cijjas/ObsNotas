- Pequeño texto de información enviada por el servidor y almacenada por el browser
- Usadas para mantener un estado entre el cliente y el servidor
	- Servidor envía cookie a cliente HTTP ( «set-cookie» response header)
	- Cliente HTTP retorna cookie al servidor ( «cookie» request header)
- Persistencia (tiempo de guardado)
	- Session cookie
	- Persistent cookie
- Third-party cookie
- Secure cookie

Las cookies mantien las seciones logged-in por ejemplo.
![[Pasted image 20230811190418.png]]

#### Ejemplo
> GET
> host: abc.com 
> Trae cookies

> GET
> host: abc.com
> Envia cookies