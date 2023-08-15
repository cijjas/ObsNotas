[Guía 2](https://docs.google.com/document/d/1MFaBmZf-hTo4CGgp1LDpLWnQ275fQq2Bw44vvEeGkCo/edit#heading=h.gjdgxs)
[Guía 2 Soluciones](https://docs.google.com/document/d/1AinwDLftLGO2TeMooyUtQJXuJLEFRvWzfby6SXQj0w4/edit)


# 1
> ¿De qué forma puede un Proxy HTTP saber que para el recurso que le solicita un cliente aún es válida la copia que tiene en caché?

Hay dos opciones, una es con el [[Proxy Servers#max-age]] , otra con [[Proxy Servers#last-modified]] y otra con una combinación de ambas.

# 2
> El modelo de capas TCP/IP no ofrece un nivel de Sesión. El protocolo HTTP no es orientado a conexión. ¿Cómo puede entonces una aplicación web mantener una “sesión” abierta?

Mediante el uso de [[Cookies]] se puede simular mantener una sesión abierta. 

# 3
> ¿Es correcto afirmar que “la única posibilidad de solicitar un recurso desde mi browser y obtenerlo sin acceder al servidor HTTP es porque el proxy tiene una copia del mismo”?

No solo el Proxy puede tener una copia guardada en cache sino el browser en sí también.

# 4
> Una empresa tiene una aplicación web interna, que –por cuestiones de seguridad- sólo acepta conexiones desde el proxy. A fin de asegurarse que quien se conecta sea realmente el proxy, espera en el encabezado una frase secreta usando un “custom header”, por ejemplo una línea conteniendo el encabezado “X-PHRASE:I AM THE PROXY”. En este servidor HTTP, ¿habilitaría o no la opción TRACE?

No debería habilitarla en el servidor HTTP, ya que la opción TRACE hace que el cliente reciba en el cuerpo el encabezado recibido por el servidor (no el proxy). Como el servidor recibió el encabezado agregado por el proxy, el cliente se enteraría cuál es la frase secreta. Esto ocurre por ejemplo como se muestra en el ejemplo [[Guía#28]] donde se obtiene [[Guía#405 Not allowed]].

# 5

> Indicar si las siguientes afirmaciones son válidas o no
> - HTTP es un protocolo de texto
> - MIME es un protocolo que pertenece a la capa de presentación del modelo OSI
> - “Third party cookies” hace referencia a una cookie que un servidor HTTP deja para ser enviada luego a otro servidor HTTP

1. Depende de la versión. La versión 2 es binaria, las anteriores de texto
2. Verdadero
3. No es válida, ya que las cookies de un recurso sí o sí están relacionadas con el servidor en el cual el recurso está alojado.

# 6

> ¿Por qué puede ser que algunos recursos -por ejemplo imágenes- que se obtienen de un mismo servidor HTTP se guardan en la caché y otras no, siendo que todos ellos tienen  el mismo header de Cache-Control ?

Una razón es que algunos recursos se obtuvieron con el comando GET mientras que otros fueron solicitados con el comando POST.

# 7
> Si un recurso enviado por un servidor HTTP es cacheado en mi browser, ¿significa eso que también será cacheado en mi proxy? Para poder responder correctamente ver [Private vs Public cache](https://stackoverflow.com/questions/3492319/private-vs-public-in-cache-control)

> The only difference is that with Private you are not allowing proxies to cache the data that travels through them. In the end, it all boils down to the data contained in the pages/files you are sending.
> 
> For example, your ISP could have an invisible proxy between you and the Internet, that is caching web pages to reduce the amount of bandwidth needed and lower costs. By using cache-control:private, you are specifying that it shouldn't cache the page (but allowing the final user to do so). If you use cache-control: public, you are saying that it's okay for everyone to cache the page, and so the proxy would keep a copy.
> 
> As a rule of thumb, if it's something _everybody_ can access (for example, the logo in this page) cache-control: public might be better, because the more people that cache it, the less bandwidth you'll need. If it's something that is related to the connected user (for example, the HTML in this page includes my username, so it won't be useful to anyone else) cache-control: private will be better, as the proxies would be caching data that won't be requested by other users, and they might also be keeping data that you don't want to be kept in servers that you don't trust.
> 
> And, of course, everything that is not public should have a private cache. Otherwise the data might be stored in a middle proxy server, were it could be accessed by anyone with access to it.



