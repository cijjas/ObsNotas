![[Final_23-7-10[1].pdf]]

## Ejericicio Sincronización
Cada iteracion i debe correr los n foo primero antes que los n bar.
```c
semaphore mutex = 1;
semaphore barSem = 0;
semaphore iteracion = 1;
int pending = N;

void proceso_n(){
	while(1){
		
		foo();
		
		down(mutex);
		pending--;
		if (pending == 0){
			pending = N; 
			up(barSem); // levanto el semaforo para que se ejecuten los bars
			down(iteracion);
		}
		up(mutex);
		
		down(barSem);
		up(barSem);
		
		bar();
		
		down(mutex);
		pending--;
		if (pending == 0){
			pending = N;
			up(iteracion); 
			down(barSem);
		}
		up(mutex);
		
		down(iteracion);
		up(iteracion);
		
	}
}
```