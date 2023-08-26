Estándar de presentación

> Los media types proporcionan una forma estandarizada de comunicar el tipo de contenido entre diferentes sistemas y aplicaciones, lo que facilita la correcta interpretación y manejo de los datos en el entorno de la web.

- Contenido multimedia
- Cada objeto es etiquetado por el web server con su tipo y subtipo
	- text/html
	- text/plain
	- video/mp4
	- image/jpeg
	- application/pdf
![[Pasted image 20230825175652.png]]
## SMTP no puede transmitir objetos binarios. 
- SMTP no puede transmitir texto que incluya caracteres nacionales
- Los servidores SMTP pueden rechazar los mensajes que superen un tamaño concreto. 
- Algunas implementaciones de SMTP u otros MTAs de Internet no respetan por completo el estándar SMTP. Algunos problemas son: 
	- Eliminación de espacios al final de la línea
	- Relleno de todas las líneas de un mensaje para que tengan la misma longitud. 
	- Conversión de caracteres TAB a múltiples caracteres SPACE.

![[Pasted image 20230825174407.png]]


> 
(Multipurpose Internet Mail Extensions Encoding ) respeta el RFC 822. Agrega una estructura al cuerpo del mensaje, por lo que es transparente para SMTP. Permite:

-  Normalizar intercambio de diferentes tipos de contenido (texto simple, texto formateado, imágenes, sonido, video y documentos HTML).
-  Solucionar el problema de enviar texto internacional por mail.


# Técnicas para autenticar mails

> Según Verizon el 30% de los mails de phishing se abren, y en hasta un 12% de ellos se accede a los enlaces o archivos maliciosos

- Hay dos técnicas principales para autenticar mails
	- SPF (Sender Policy Framework)
		- Permite detectar qué servidor o servidores tienen permiso para enviar mails en su nombre.
		- Su función es evitar que un mail sea enviado desde servidores que no estén relacionados con el dominio.
		- Se utilizan registros TXT y SPF en el servidor DNS
		- ![[Pasted image 20230825180728.png]]
	- DKIM (DomainKeys Identified Mail)
		- ![[Pasted image 20230825180742.png]]



# Material de lectura
Capítulo 2.4 de la bibliografía
[DKIM](https://postmarkapp.com/guides/dkim)
[SPF](https://postmarkapp.com/guides/spf)
[DMARK](https://www.sparkpost.com/resources/email-explained/dmarc-explained/)
