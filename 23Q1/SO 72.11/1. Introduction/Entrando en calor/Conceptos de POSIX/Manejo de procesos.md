
![[Pasted image 20230713105905.png]]
![[Pasted image 20230713105927.png]]


## Fork
La función "fork" se utiliza en sistemas operativos Unix y Unix-like para crear un nuevos [[Procesos]]. Cuando se invoca la función "fork", se crea una copia exacta del proceso existente, incluyendo el código, los datos y el estado actual del proceso. La copia resultante se denomina proceso hijo, mientras que el proceso original se conoce como proceso padre. El proceso hijo tiene un ID de proceso (PID) único y comparte ciertos recursos con el proceso padre, como archivos abiertos y variables compartidas.

- Crea un clon exacto del caller. Luego de fork, los dos procesos (el padre y el hijo) tienen lamisma memoria, las mismas variables de ambiente y los mismos archivos abiertos.

## Execve 
La función "execve" se utiliza para ejecutar un programa en un proceso existente. Permite cargar y ejecutar un nuevo programa en el espacio de memoria del proceso actual, reemplazando el programa existente. La función toma como argumentos la ruta del programa a ejecutar, un array de argumentos y un array de variables de entorno. Al invocar "execve", se carga el programa especificado en el espacio de memoria del proceso y se inicia su ejecución, reemplazando completamente el código y los datos anteriores.

- Cambia completamente la imagen del proceso. Esto incluye memoria (heap, stack, código),registros (de propósito general y especiales). Pero preserva archivos abiertos entre otras cosas.

## Waitpid
La función "waitpid" se utiliza para esperar a que un proceso hijo termine su ejecución en un proceso padre. Permite al proceso padre suspender su ejecución hasta que uno de sus procesos hijos termine. La función "waitpid" toma como argumentos el PID del proceso hijo que se desea esperar y un puntero a una variable entera donde se almacenará el estado de salida del proceso hijo una vez que haya terminado. Al utilizar "waitpid", el proceso padre se bloqueará hasta que el proceso hijo especificado termine y se puede obtener información sobre su estado de salida.

## Exit
La función "exit" se utiliza para finalizar la ejecución de un proceso. Al invocar "exit", el proceso actual se detiene y se libera toda la memoria y los recursos que le pertenecen. También se envía un código de salida al sistema operativo, que indica el estado de salida del programa. El código de salida se puede utilizar para determinar si el programa finalizó correctamente o si ocurrió algún error. Después de llamar a "exit", el proceso se termina y devuelve el control al sistema operativo.
![[Pasted image 20230713133549.png]]