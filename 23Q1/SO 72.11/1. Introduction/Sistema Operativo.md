![[Pasted image 20230713095041.png]]

Tiene como objetivo administrar los recursos de hardware creando una [[Abstracción]] para estos.

## Hardware
Revisando el hardware de un sistema operativo 
- [[Procesador]]
- [[Memoria]]
- [[Disco]]
- [[Dispositivos IO]]
- [[BIOS]]

## Diferentes Sistemas Operativos
El zoológico de los Sistemas Operativos
![[Pasted image 20230713102846.png]]
- **Mainframe**: Mucho almacenamiento y memoria. Orientado a muchos procesos. Soporta trabajos porlotes, transacciones y timesharing. OS/390, tendencia a UNIX.
- **Server**: Computadoras personales o incluso mainframes. Impresoras, archivos o webs. Solaris,FreeBSD, Linux y Windows Server.● Multiproceso: (Necesaria la separación)
- **Personal Computer**: Proveer soporte a un único usuario. Linux, FreeBSD, Windows y Apple’s OS X.
- **HandHeld Computer**: Tablets y smartphones. Android y iOS
- **Embedded**: Electrodomésticos y teléfonos antiguos. ROM, no permite la instalación de aplicaciones.Embedded Linux, QNX y VxWorks.
- **Sensor-node**: Redes de nodos. Poseen CPU RAM y ROM. Sensan diferentes condiciones. Conexióninalámbrica. TinyOS
- **Real Time**: Necesitamos que una acción ocurra en un momento específico. hard vs soft. Industria,aviónica, milicia y multimedia. eCos y FreeRTOS
- **Smart Card**: Pagos electrónicos. Del tamaño de una tarjeta de crédito. Restricciones de potencia y memoria muy altas. Obtienen energía por inducción o al conectarse a un lector.

## System Calls

El sistema operativo utiliza [[System Calls]] para abstraer el Userland del Kernel. De esta forma logra usar los recursos del Kernel sin tener que entenderlos internamente.


## Estructura de un Sistema Operativos

- Monolithic systems
	- ![[Pasted image 20230713103857.png]]
- Layered systems
	- ![[Pasted image 20230713103908.png]]
- Microkernels
	- ![[Pasted image 20230713103919.png]]
	- ![[Pasted image 20230713104122.png]]
	- ![[Pasted image 20230713104306.png]]
- Client-server systems
	- ![[Pasted image 20230713103950.png]]
- Virtual machines
	- ![[Pasted image 20230713104004.png]]
	- ![[Pasted image 20230713104019.png]]
- Exokernels
	- ![[Pasted image 20230713104038.png]]


- Monolithic vs MicroKernels
	- ![[Pasted image 20230713104225.png]]


***

### [[Ejercicios INTRO]]

### Finales
[[Final.pdf]]
[[Final 1F-2023]]
[[Final Febrero 2022]]
[[Final_23-7-10[1].pdf]]
