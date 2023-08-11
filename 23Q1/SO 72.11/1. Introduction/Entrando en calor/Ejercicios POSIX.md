1. Escribir un programa en C que liste recursivamente el contenido de un directorio que recibe como primer y único argumento, indicar sicada elemento es un archivo o un directorio, tabular la salida por nivel de anidamiento (stat opendir readdir)Ejemplo de la salida (solo a modo ilustrativo): ![[Pasted image 20230713111940.png]]
2.  Ejercicio 2
	1. Escribir un programa en C que lance 10 procesos que realicen alguna tarea que dure una cierta cantidad de tiempo considerable(por ejemplo, dormir una cantidad al azar de tiempo), el programa debe esperar a que sus procesos hijos terminen para terminarél mismo. (fork waitpid).
	2. Hacer que cada hijo imprima su propio pid (getpid)
	3. Separe el código de los hijos y del padre en dos unidades de compilación diferentes (execve)
3. Lance varios procesos hijos desde un padre, haga que el padre centre en un loop infinito sin hacer waitpid, mientras que sus hijosterminan instantáneamente, salvo 1 que también quedará en un loop infinito. Para observar el estado de los procesos se recomienda ejecutar: $ ps ax -O "%P"
	1. ¿Qué imagina que va a pasar con los procesos hijos que terminaron? ¿Por qué cree que pasa?
	2. Mate el proceso padre (kill) ¿Qué sucede?
	3. ¿Cambió algo para el proceso hijo que estaba en un loop luego de matar al padre?
	4. ¿Qué es el proceso init?
	5. ¿Qué pasa en los sistemas POSIX con los procesos huérfanos?
	6. ![[Pasted image 20230713112302.png]]
4. Dados los programas dentro del repositorio ejemplos/producer-consumer y la resolución del inciso 3 del ejercicio 2:
	1. Modifique la resolución del inciso 3 del ejercicio 2, de manera tal que el proceso padre ejecute p y c (fork y exec) conectando elstdout de p al stdin de c utilizando un pipe (pipe).
	2. Modifique la resolución del inciso 3 del ejercicio 2, de manera tal que el proceso padre ejecute p en background.
	3. Modifique la resolución del inciso 3 del ejercicio 2, de manera tal que el proceso padre ejecute p y redireccione stdout a unarchivo. (close y open)
	4. Modifique la resolución del inciso 3 del ejercicio 2, de manera tal que el proceso padre ejecute c, pero que en lugar de leer destdin lea de un archivo.
5. Modifique la resolución del inciso 3 del ejercicio 2, de manera tal que el proceso padre ejecute 2 programas de forma secuencialconsiderando 3 escenarios posibles
	1. INCONDICIONAL, primero ejecuta un proceso y cuando termina ejecuta el otro.
	2.  AND, si el primer proceso falla (exit status != 0), NO se ejecuta el segundo
	3. OR, si el primer proceso termina satisfactoriamente (exit status == 0), NO se ejecuta el segundo
	Puede utilizar los programas true.c y false.c para hacer pruebas. (hint: man true, man false)(wait)
6. ![[Pasted image 20230713112552.png]]

