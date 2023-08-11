
Tradicionalmente un proceso tiene su espacio de direcciones y un único hilo (thread) de ejecución.
  
Existen casos en los que es muy útil tener múltiples hilos en un mismo espacio de direccionescorriendo de forma pseudo paralela como si fueran procesos separados, salvo por el espacio dedirecciones


### ¿Por qué queremos threads?
![[Pasted image 20230713191538.png]]


### Ejemplo Web Server
Por ejemplo hay 3 threads (Workers) donde cada uno atiende una tarea diferente:
- Atender conexiones
- Enviar páginas en cache
- Buscar páginas en disco (bloqueante)

![[Pasted image 20230713191709.png]]

![[Pasted image 20230713191722.png]]

![[Pasted image 20230713191946.png]]


### [[Procesos]] vs Threads

Threads $\subset$ Procesos pero:

Procesos | Threads
-- | --
agrupa recursos | entidad programada para ejecución en CPU
comparte la memoria, dispositivos de entrada y salida, etc | comparte el espacio de direcciones, files, señales, etc

Los threads permiten multiples ejecuciones en el mismo conjunto de recursos.

> Threads are light weight processes


### Modelo de threads
![[Pasted image 20230713192758.png]]

![[Pasted image 20230713192837.png]]


### Uso de Threads en [[POSIX]]
![[Pasted image 20230713193009.png]]
![[Pasted image 20230713193117.png]]





### Implementación en Userspace vs Kernel
Hay 3 formas de implementar threads
* [[Userspace managed threads]]
* [[Kernel managed threads]]
* [[Hybrid managed threads]]

***
### [[Ejercicios THREADS]]
