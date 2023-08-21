- Permite que 2 procesos se comuniquen bajo el esquema productor-consumidor
- Uno de los primeros mecanismos de IPC en UNIX
- Buffering: acotado (como en el tp que hicimos un vector circular que es un buffer)
- Sincronización: send bloquea al llenarse el pipe, receive bloquea hasta que haya algo

![[Pasted image 20230713145150.png]]

### Categorización
![[Pasted image 20230713145338.png]]
#### Pipes Anónimos u Ordinarios (sin nombre)
A diferencia de un pipe con nombre (named pipe o FIFO), que tiene un nombre en el sistema de archivos y se utiliza para comunicación entre procesos no relacionados, un pipe anónimo se establece directamente entre dos procesos relacionados, generalmente a través de un proceso padre e hijo o entre procesos creados por una llamada al sistema "fork".

El uso de pipes anónimos es útil cuando se necesita establecer una comunicación simple y rápida entre dos procesos relacionados. Puede ser utilizado para pasar información, como datos o comandos, desde un proceso a otro de manera eficiente y sincronizada.

![[Pasted image 20230713145512.png]]

Es importante destacar que los pipes anónimos solo permiten la comunicación unidireccional y en un sentido. Si se requiere comunicación bidireccional o entre más de dos procesos, se pueden utilizar múltiples pipes anónimos o considerar otros mecanismos de IPC más complejos, como sockets de dominio Unix.

#### Pipes con nombre
Los pipes con nombre (named pipes o FIFO, por sus siglas en inglés) son un mecanismo de comunicación interprocesos (IPC) que permite la transferencia de datos entre procesos, al igual que los pipes anónimos. Sin embargo, a diferencia de los pipes anónimos, los pipes con nombre tienen un nombre asociado y se crean en el sistema de archivos como un archivo especial.

Un pipe con nombre se establece entre dos o más procesos, generalmente no relacionados entre sí, que desean comunicarse. Se crea utilizando el comando `mkfifo` en sistemas operativos tipo UNIX, que crea un archivo especial FIFO en el sistema de archivos.

### Funcionamiento
![[Pasted image 20230713110610.png]]
![[Pasted image 20230713110627.png]]



### Funcionamiento dup
![[Pasted image 20230713110743.png]]
![[Pasted image 20230713110755.png]]![[Pasted image 20230713110803.png]]![[Pasted image 20230713110812.png]]![[Pasted image 20230713110821.png]]![[Pasted image 20230713110830.png]]