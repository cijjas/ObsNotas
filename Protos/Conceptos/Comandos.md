```bash 
echo hola | od -txl
```
- od me muestra los bytes
- aparecen en ascii los 5 caracteres de hola + el \n 
- para scar el \n hago echo -n hola

## Convertir de una codificación a otra

```bash 
echo -n mi_icono | iconv --from-code=utf-8 --to-code=UTF-32BE | od -txl
```
## Redireccionar salida a otro archivo >>

```bash
echo hola >> archivo.txt 
;ver lo que tiene ese archivo: cat archivo.txt
```
## tail : Para ver los cambios en ese archivo
```bash
tail -f
```
- con -f abre el archivo y se queda viendolo (follow) 
- con -n3 agarra las ultimas 3 lineas del archivo

## Ir agarrando las primeras lineas

```bash
head -n1
```
-n1 me da la primera linea, -n2 las primeras 2

```bash
more  y less por ejemplo
tree | less
```
## find: Encontrar archivos

```bash
find 
locate
```
## Saber si cosas estan corriendo
```bash
ps combinar con otros para busquedas especificas 
ps aux | grep sleep 
ps auxf | less
```

## Como pasamos de un usuario a otro
```bash
sudo su - nombre_user
```
- primero nos pasamos al user admin (sudo), con el nos podemos pasar a cualquier otro user

```bash
sudo service nginx start
```
## xargs : Para agregar mas argumentos
```bash
xargs echo hola
```
## [[Netcat]]
```bash
nc -l 9090 # listening
nc 127.0.0.1 9090 #writing to 127... on port 9090
```
- -l indica que tiene que estar listening
- socket pasivo: el que espera recibir (escucha) (trolita) 
- socket activo: EL MACHO

## [[cURL]]