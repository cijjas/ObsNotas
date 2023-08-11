Situación en la programación concurrente donde el comportamiento o resultado de un programa depende del orden y la sincronización no determinista de las operaciones entre múltiples hilos o procesos. 

![[Pasted image 20230713152200.png]]

### Ejemplo 1
```c
/*
 * 2 instancias de home banking intentando debitar
 */
int saldo_en_cuenta;
void debitar(int *saldo, int debito){
	if (*saldo >= debito)
		*saldo -= debito;
	}
}
```
![[Pasted image 20230713152011.png]]

En este caso la [[Región Crítica]] es 
```c
if (*saldo >= debito)
	*saldo -= debito;
}
```

#### Solución
![[Pasted image 20230713152720.png]]

Una solución con semaforos sería:
```c
int saldo_en_cuenta;
semaphore mutex = 1;
void debitar(int *saldo, int debito){
	down(mutex);
	if (*saldo >= debito)
		*saldo -= debito;
	up(mutex);
}
```



### Ejemplo 2
```c
#define N 100 /* número de ranuras en el búfer */
int cuenta = 0; /* número de elementos en el búfer */
void productor(void)
{
	int elemento;

	while (TRUE) { /* se repite en forma indefinida */
		elemento = producir_elemento(); /* genera el siguiente elemento */
		if (cuenta == N) sleep(); /* si el búfer está lleno, pasa a inactivo */
		insertar_elemento(elemento); /* coloca elemento en búfer */
		cuenta = cuenta + 1; /* incrementa cuenta de elementos en búfer */
		if (cuenta == 1) wakeup(consumidor); /* ¿estaba vacío el búfer? */
	}
}
void consumidor(void)
{
	int elemento;
	
	while (TRUE) { /* se repite en forma indefinida */
		if (cuenta == 0) sleep(); /* si búfer está vacío, pasa a inactivo */
		elemento = quitar_elemento(); /* saca el elemento del búfer */
		cuenta = cuenta – 1; /* disminuye cuenta de elementos en búfer */
		if (cuenta == N – 1) wakeup(productor); /* ¿estaba lleno el búfer? */
		consumir_elemento(elemento); /* imprime el elemento */
	}
}
```

Acá hay una race condition escondida, el caso patológico viene de la situación especifica en la cual el buffer esta vacío, el consumidor checkea si `cuenta == 0` apenas checkea hace un context switch en el cual salta el productor, el productor termina de producir y ahora `cuenta == 1` . El productor intenta de hacer `wakeup(consumidor)` pero como el consumidor todavía no ejecutó `sleep()` entonces esta señal se pierde. Cuando es turno de que se ejecute el consumidor, evalúa el valor de cuenta que leyó antes, encuentra que es 0 y pasa a dormirse. Tarde o temprano el productor llenará el búfer y también pasa a dormirse. Ambos quedan dormidos para siempre.

Una solución con semáforos: 
```c
#define N 100 /* número de ranuras en el búfer */
typedef int semaphore;
semaphore mutex = 1; /* acceso exclusive a la región critica */
semaphore empty = N; /* cuenta la cantidad de espacios libres */
semaphore full = 0;  /* cuenta la cantidad de espacios ocupados */

void productor(void)
{
	int elemento;

	while (TRUE) { /* se repite en forma indefinida */
		elemento = producir_elemento(); /* genera el siguiente elemento */
		
		down(&empty);
		down(&mutex);
		
		insertar_elemento(elemento); /* coloca elemento en búfer */
		
		up(&mutex);
		up(&empty);
	}
}
void consumidor(void)
{
	int elemento;
	
	while (TRUE) { /* se repite en forma indefinida */
		down(&full);
		down(&mutex);
		
		elemento = quitar_elemento(); /* saca el elemento del búfer */
		
		up(&full);
		up(&empty);
		
		consumir_elemento(elemento); /* imprime el elemento */
	}
}
```
### Introducción de [[Semáforos]]
De acá sale una propuesta de Dijkstra para generar un "Wakeup waiting bit" que luego serían llamados [[Semáforos]].