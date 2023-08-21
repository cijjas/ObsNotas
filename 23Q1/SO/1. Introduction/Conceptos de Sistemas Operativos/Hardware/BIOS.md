  
### La placa madre posee un programa llamado BIOS
  
La BIOS posee instrucciones para interactuar con la pantalla, teclado y disco

Cuando se enciende una computadora
1. Chequear cuánta memoria tenemos y si ciertos dispositivos como el teclado están instalados y responden correctamente.
2. Escanea buses PCIe y PCI en busca de dispositivos instalados.
3. Determina el dispositivo de booteo.
4. Se carga el primer sector en memoria y se ejecuta
5. Este sector suele leer una tabla de particiones y se se carga un segundo sector
6. Se carga en memoria el SO y se ejecuta.
7. El SO consulta a la BIOS los dispositivos conectados