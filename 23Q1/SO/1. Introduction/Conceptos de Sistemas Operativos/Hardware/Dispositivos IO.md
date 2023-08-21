Cada dispositivo se puede dividir en 2 partes :
1. Controlador ([[Abstracción]])
2. Dispositivo


  Como se utilizan en un SO:
1. El driver le indica al controlador qué hacer. Este inicia la operación en el dispositivo.
2. El controlador señaliza al controlador de interrupciones (CI).
3. Cuando el CI está listo (otras interrupciones) setea el pin correspondiente en el CPU
4. El CI escribe el número de dispositivo (vector de interrupciones) en el bus.