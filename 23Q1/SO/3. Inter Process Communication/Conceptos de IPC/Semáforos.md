Los semáforos son una herramienta de sincronización utilizada para coordinar y controlar el acceso concurrente a recursos compartidos entre [[Procesos]] o [[Threads]]. 

Hay dos tipos principales de semáforos:
1. **Semáforo binario**: Es un semáforo con dos posibles valores: 0 y 1. También se conoce como semáforo mutex (mutual exclusion). Se utiliza para lograr exclusión mutua, es decir, garantizar que solo un proceso o hilo pueda acceder a un recurso compartido a la vez. Cuando un proceso adquiere el semáforo, su valor se establece en 1 y otros procesos que intenten adquirirlo se bloquean hasta que el semáforo se libere.
2. **Semáforo contador**: Es un semáforo con un rango de valores no negativos. Se utiliza para controlar el acceso a un número limitado de recursos, como un conjunto de hilos o un conjunto de conexiones a una base de datos. Cada vez que un proceso adquiere el semáforo, su valor se decrementa. Si el valor es 0, el proceso se bloquea hasta que otro proceso libere el semáforo y su valor sea mayor que 0.


Se proponen 2 operaciones:
- **down** : (sleep) atómicamente decrementa el semáforo o bloquea al caller si ya es 0
- **up** : (wakeup) atómicamente incrementa el semáforo y desbloquea a algún bloqueado si existe