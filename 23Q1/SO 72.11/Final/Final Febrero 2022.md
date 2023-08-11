

![[Final.pdf]]



1. El problema es que cuando es la apertura de sucursales, cuando una sucursal esta ejecutando el código, esta impide que el proveedor actualice el precio. Entonces siempre hay una preferencia para que la sucursar consulte los precios antes de que el proveedor pueda actualiza. En el código, la sucursal entra en la zona crítica que es el precio (ver el precio) y cuando entre inicializa un contador que cuenta la cantidad de sucursales consultando el precio. Solo se libera el semaforo b si ya no hay más sucursales consultando. 

Existen muchas formas de evitar que las sucursales tengan siempre preferencia por sobre los proveedores.

Una forma es:
- Haciendo una especie de barrera que ponen los proveedores apenas hay uno esperando para que no pasen nuevas sucursales. Que cuando aparezca uno se espera hasta que las actuales sucursales terminen y entonces pueden actualizar los precios.

```c
sem_t sem_a = 1; // Asumimos que sem_t funciona como un int
sem_t sem_b = 1;
sem_t sem_c  = 1;
int sc = 0;

void sucursal() {
	while (1) {

		sem_wait(&sem_c);
		sem_post(&sem_c);
		
		sem_wait(&sem_a); 
		if(++sc == 1) sem_wait(&sem_b);
		sem_post(&sem_a);
		
		consultar_precios_en_casa_central();
		
		sem_wait(&sem_a);
		if(--sc == 0) sem_post(&sem_b);
		sem_post(&sem_a);
		
		actualizar_precios_localmente();
	}
}
void proveedor() {
	while (1) {
		calcular_aumento_de_precios();
		
		sem_wait(&sem_c);
		sem_wait(&sem_b);
		
		actualizar_precios_en_casa_central();
		
		sem_post(&sem_b);
		sem_post(&sem_c);
	}
}
```

2. 
```bash
make 2>&1 | grep "warning" | nauniq
```

3. 