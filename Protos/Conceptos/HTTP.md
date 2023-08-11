[[Protos/Material/Presentaciones#2 HTTP]]

# Antes de HTTP
- Vía FTP se obtenía un documento o texto
- En base a las referencias se debía acceder a otro sitio FTP y descargar el/los textos deseados
- Surge la necesidad de aplicaciones basadas en "hipertextos"
![[Pasted image 20230804194447.png]]
# HTTP 0.9 (1991)
> En una época donde no había nada de seguridad y todo era lento. Además solo GET
- Protocolo **basado en texto** (el intercambio de información es de texto) de recuperación de información
- Mecanismo *request – response*
- Contenido estático
- No mantiene estado (no establece una sesión)
- Orientado a "línea de comando"
![[Pasted image 20230804194507.png]]


# HTTP 1.0 (1996)
> Un request por CADA recurso (no confundir con "página web")
- "Browser friendly"
- Comandos como **GET, POST, HEAD**
- Códigos de estado
- No solo hipertexto
![[Pasted image 20230804194742.png]]

# HTTP 1.1 (1999)
> Cada recurso se identifica con una URI (Uniform Resource Identifier )
- **Contenido dinámico**
- Cabeceras en las peticiones
- Métodos **PUT, DELETE, TRACE, OPTIONS**
- Negociación de contenido
- Soporte de cache
- Conexiones persistentes
![[Pasted image 20230804195117.png]]