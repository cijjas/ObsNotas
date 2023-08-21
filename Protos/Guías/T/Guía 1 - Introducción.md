
![[01 Introduccion - Guía de ejercicios.docx]]

![[01 Introducción - Respuestas.docx]]
![[Pasted image 20230805211923.png]]
1. Sean dos hosts que están en dos redes contiguas, como en la imagen superior. Se sabe que el ancho de banda entre el host de la izquierda y el router es de 10mbps (1000 bits por segundo), y entre el router y el host de la derecha es de 20mbps. Si el primer host decide enviarle al segundo un paquete que en total (datos + encabezados) es de 100 Bytes, ¿podría calcular el tiempo exacto que va a demorar desde que se envía el primer bit del primer host hasta que el último bit arriba al segundo host? En caso afirmativo, indicar cuánto sería en total ese tiempo, en caso negativo explicar por qué no se puede calcular en forma exacta.
	1. La respuesta es que no se puede calcular el tiempo pues no se puede calcular la latencia (retraso en la transmisión de datos a través de una red, puede influir el tipo de medio de comunicación, distancia física, congestión y otros ). Otros factores serían el tiempo que toma el router en procesar y si hay encolamiento.
	2. En el caso hermoso que todo es arcoíris y ponys 
		1. $R_1 =  10mbps$
		2. $R_2 = 20mbps$
		3. $L = 100 ~ Bytes$ 
		4. Mirar [[Red de Computadoras#Como envía el host]]
		5. $t = \frac{L}{R}$ 
		6. Empieza el temporizador, cuando el paquete llega al router, se transmitió en $t_1 =\frac{100B}{10mbps}$ luego cuando llega al segundo se tardo un adicional de $t_2= \frac{100B}{20mbps}$
		7. Luego $t = t_1 +t_2 = \frac{100 *8 b}{1000 \frac{b}{s}} += \frac{100 *8 b}{2000 \frac{b}{s}} = \frac{8}{10}s + \frac{8}{20}s = \frac{24}{20}s = 1.2s$
2. VoF
	1. **Si el protocolo de una capa del [[Red de Computadoras#Modelo OSI (1984)]] es orientado a conexión, enftonces la capa superior también ofrecerá un servicio orientado a conexión.**
		1. FALSO Que un protocolo sea orientado a conexión implica que antes de enviar información se debe establecer una conexión o sesión. Por ejemplo [[HTTP]] utiliza [[Red de Computadoras#TCP/IP]] y es un protocolo de aplicación que no requiere establecer una sesión, a diferencia de otros como FTP, SMTP, etc.
	2. **Un router conecta 2 o más redes**
		1. VERDADERO, por lo menos se conecta al [[Red de Computadoras#LAN]] y al ISP (Internet Service Provider).
		2. LocalAreaNet <-----> WideAreaNet
	3. **Si el protocolo de una capa del modelo OSI es sin conexión y no confiable, entonces la capa superior no puede garantizar la recepción de los mensajes enviados.**
		1. FALSO. Si fuera verdadero todos los protocolos de transporte y por extensión los de aplicación deberían ser sin conexión y no confiables, ya que IP lo es. Si la capa inferior no ofrece un servicio confiable o con conexión entonces la capa superior puede implementarlo (por ejemplo TCP)
		2. El truquito está en que la capa superior no depende de la orientacion del inferior
	4. **Un protocolo confiable es aquel que asegura que los datos lleguen correctamente a destino**
		1. FALSO, confiable es que hay información en cuanto a la recibida del mensaje, sea que se recibió o que no. No asegura que lleguen correctamente solo asegura tener información sobre la recibida.
	5. **Si un protocolo de aplicación utiliza un protocolo de transporte no orientado a conexión, entonces puede recibir los datos en orden distinto al que fueron enviados**
		1. VERDADERO al parecer ni idea
	6. **Si un paquete debe llegar desde el host A hasta el host Z pasando antes por los host M y N, y se sabe que el protocolo de enlace entre A y M, M y N, y entre N y Z son confiables, entonces podemos decir que el protocolo de red entre A y Z también será confiable.**
		1. FALSO, A no puede saber si Z recibió, solo puede saber si M recibió. No es transitivo de esa forma 
	7. **Si en una red cableada hay 4 computadoras que deben acceder a otras redes, entonces el router tendrá que tener al menos 4 interfaces.**
		1. FALSO, cada interfaz se conecta a una red, se tienen que conectar a un switch las 4 compus y hay una interfaz más para el router, por ende hay 5 interfaces
3. **¿Es lo mismo un [[Red de Computadoras#Medio de comunicación Broadcast]] que una [[Red de Computadoras#Comunicación Broadcast]]?**
	1. El medio es específico para un conjunto del total de los receptores. Por otro lado la Comunicación Broadcast es un comunicado sin target específico del conjunto de receptores. 
4. VoF
	1. **Si en una red todas las PCs están interconectadas con un hub, entonces cualquiera de ellas puede ver los mensajes que envían y reciben el resto de las PCs**
		1. VERDADERO, todo lo que recibe, se lo envía a todos
	2. **Si en una red todas las PCs están interconectadas con un switch, entonces una PC sólo podría ver los mensajes que la tienen como destino a nivel de enlace (la MAC destino del mensaje es la MAC de la PC)**
		1. FALSO, También podría ver los mensajes broadcast y aquellos cuya MAC de destino el switch aún no aprendió en qué interfaz está conectado.
	3. **Si en una red reemplazamos el hub por un switch es muy probable que aumente la velocidad de las comunicaciones.**
		1. VERDADERO pero DEPENDE (poneeele....) El switch permite que haya mucho menos colisiones de mensajes y por ende aumente la velocidad de comunicación, (además, truquito, el switch permite hacer mensajería simultanea, o sea se pueden resolver mensajes de A a B mientras se hacen de C a D). Cuestión que está este caso de cuando en realidad no hay tanta denisdad de mensajes (poco uso del cable de red) entonces en realidad no es necesario todo esto y sería overkill. Por ende en la mayoría de los escenarios el enunciado es verdadero 

