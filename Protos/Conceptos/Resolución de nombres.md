# Dominio
> Un dominio es una coleccion de computadoras que pueden ser acedidas usando un nombre en común.


# Nombre de dominio
> Hace referencia al nombre de múltiples hosts que son referenciados colectivamente. ()

> Dentro de un top-level domain, una organización tiene su propio dominio o dominios. A su vez dentro del dominio puede haber sub-dominios. Y cada host tiene su nombre propio (hostname).

Uniendo el nombre del host con el dominio al cual pertenece se forma el FQDN (fully qualified domain name).

![[Pasted image 20230818170729.png]]

# Obtención de IP con un FQDN

## /etc/hosts 
El nombre figura en el archivo /etc/hosts
![[Pasted image 20230818170854.png]]
- Por defecto se consulta primero este archivo y luego DNS
- Se puede cambiar el orden en /etc/nsswitch.conf
## /etc/resolv.conf

![[Pasted image 20230818171240.png]]
- También hay cache en [[DNS]] para nombres de dominios.
- **nameserver** *direcciones*
	- Números IP de los servidores de nombres que consultara el resolver (hasta 3). Si no hay ningún nameserver utilizará al propio host  como servidor de nombres.
- **domain** *nombre*
	- Dominio local por defecto. El resolver agrega este nombre a todo hostname que no contenga un punto antes de resolverlo.
- **search** *dominios*
	- Similar al anterior pero pueden ser varios dominios (no se usan ambas opciones en simultáneo)
- sortlist red[/mascara]
	- En caso de recibir múltiples direcciones IP para un nombre, reordena las direcciones en base a las redes listadas en esta opción.
- options opción 
	- Usada para seteos opcionales. Las posibles opciones son:
	-  debug
	-  ndots:n
	-  timeout:n
	-  attempts:n
	-  rotate
	-  no-check-names
	-  inet6



