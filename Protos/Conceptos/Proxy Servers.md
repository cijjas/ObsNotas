Un proxy server actúa como intermediario entre una aplicación cliente y un web server. Puede ser **explícito** o **transparente**.
# Conexión proxy
![[Pasted image 20230811181409.png]]
![[Pasted image 20230811181556.png]]
- El servidor proxy entiende HTTP y puede fijarse que no se permitan determinadas consultas.

# Cache proxy
Un **proxy server** permite controlar el acceso a determinados sitios o páginas, y almacenar en caché recientes consultas.
![[Pasted image 20230811182100.png]]
- Por ejemplo si muchos alumnos estamos viendo la presentación, en google slides, el proxy server guarda la pagina para darsela más rápido al que la pida.

## Sin directiva
![[Pasted image 20230811182522.png]]
## max-age
![[Pasted image 20230811182542.png]]
- Durante 600 segundos, el proxy devuelve inmediatamente
## last-modified
![[Pasted image 20230811182714.png]]
- Se fija si fue modificado el recurso en el servidor web y si no lo busca en la cache
- El fijarse si fue modificado es rápido.
- Probablemente sea valido por un tiempo pero no se por cuanto
- el Etag identifica univocamente
- En recursos muy pequeños esto no tiene sentido.
- Algo que vale la pena como imagenes y cosas grandes.
- Si lo queres tener updated
## max-age y last-modified
![[Pasted image 20230811183400.png]]
- combinación de ambos

