- **El cliente y el servidor intercambian mensajes HTTP**
	- Request message (cliente → servidor)
	- Response message (servidor → cliente)

# Solicitudes (Request)
- **GET**: Solicita un recurso al servidor
	- ![[Pasted image 20230811173245.png]]
	- En un host podria haber muchos sitios. #ParcialProtos
	- Las paginas pueden estar cargadas en un mismo IP por decir.
- **POST**: Envía información al servidor para ser procesada
	- ![[Pasted image 20230811175404.png]]
	- Tiene un body con información en al enviar al servidor.
- **HEAD**: Solicita solo los headers del recurso.
- Menos usados
	- **DELETE**: Elimina un recurso del servidor.
	- **OPTIONS**: Consulta los métodos disponibles en el servidor.
		- Opciones de acciones que se pueden hacer con ese servidor
		- ![[Pasted image 20230811180142.png]]
	- **TRACE**: Analiza el recorrido de la solicitud.
		- Puede o no ser aceptado, muestra por donde paso el request.
		- ![[Pasted image 20230811180201.png]]
	- **PUT**: Envía un recurso al servidor

### Post vs GET
- **GET requests**
	- pueden ser "cacheados"
	- el browser los mantiene en el historial
	- pueden ser "bookmarked"
	- tienen longitud acotada
	- sólo para pedir datos
- **POST requests**
	- nunca son "cacheados"
	- no se mantienen en el historial del browser
	- no pueden ser "bookmarked"
	- no tienen restricción de longitud de datos


# Respuesta (Response)
- **Start Line**: Versión, código de respuesta y mensaje.
### Códigos de respuesta
![[Pasted image 20230811174900.png]]


# [[MIME]]


# Headers
- Estructura: `<nombre>: <valor asociado>`
- Finalizan con una línea en blanco.
- En orden los tipos de headers:
	- Generales
		- ![[Pasted image 20230811180620.png]]
	- De solicitudes
		- ![[Pasted image 20230811180651.png]]
	- De respuestas
		- ![[Pasted image 20230811180703.png]]
	- De contenido
		- ![[Pasted image 20230811180720.png]]


# Ejemplo de negociación
![[Pasted image 20230811181205.png]]
- `302` te dice que lo busques en otro lado.