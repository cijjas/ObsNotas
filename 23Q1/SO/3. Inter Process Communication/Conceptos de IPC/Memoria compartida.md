Los procesos acuerdan compartir memoria física. No son necesarias las syscalls para acceder a la info. 
- La sincronización es determinada por los procesos
- Aumentan los problemas de cache coherency al aumentar los núcleos

**Permite que procesos arbitrarios compartan memoria**

![[Pasted image 20230713150517.png]]
## Files
Los archivos son memoria compartida, por ejemplo en el codigo a continuación vim puede abrir el archivo y gcc compilarlo.
```bash
vim main.c [edit]
gcc -Wall main.c
```
