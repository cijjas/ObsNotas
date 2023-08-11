Herramienta de línea de comandos para transferir recursos en base a URLs


- Incorrectos
- curl https:asite.com
- curl https:asite.com –head
- Correctos
- curl [http://google.com/humans.txt](http://google.com/humans.txt)
- curl [https://www.google.com/humans.txt](https://www.google.com/humans.txt) -i
	- -i muestra todos los headers
- curl -X POST -F 'locale=en' url
	- -F parametros del boy
