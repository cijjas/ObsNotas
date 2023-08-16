[[Presentaciones y Material#2. Automatas]]
**Máquina de estados**
> Es una quíntupla $AF = (Q, \Sigma, \delta, q_0, F)$ donde
> - $Q$ conjunto finito de estados
> - $\Sigma$ alfabeto de entrada
> - $q_0 \in Q$ estado inicial
> - $F \subseteq Q$ conjunto de estados finales o de aceptación
> - $\delta$ función de transición $(\delta : Q \times \Sigma \cup \{\lambda\} \rightarrow P(Q))$ donde $P(Q)$ denota todods los subconjuntos de Q

## Teoría de autómatas
Es el estudio de máquinas abstractas con el objetivo de modelar el funcionamiento de la computadora ideal.

> La teoría de autómatas es un campo de estudio en ciencias de la computación y matemáticas que se enfoca en el estudio de modelos abstractos de sistemas que realizan procesos de cómputo o transformación de información. Estos modelos se denominan autómatas y se utilizan para describir y analizar el comportamiento de sistemas en términos de estados, transiciones y entradas.
#### Ejemplo
![[Pasted image 20230810091410.png]]

# Función de transición $\delta$
> La función de transición de un AFD se puede representar de dos formas: mediante una tabla de transición o mediante un diagrama de transición.


- Cada círculo (nodo) representa un estado.
- Cada círculo doble representa un estado final.
- Una flecha apuntando a un estado indica que es el estado inicial.
- Cada arco dirigido representa una parte de la función de transición.
- El símbolo o etiqueta sobre el arco indica qué se consumió de la entrada al efectuar
esa transición.

![[Pasted image 20230809161729.png]]
$L = \{001, 01\}$ cualquier otra formación pertenece al [[Autómatas Finitos#Estado trampa]] y no nos interesa.

## Estado trampa
> Estado que no genera palabra (no salen flechas de él)

# Tipos de estados
![[Pasted image 20230810091449.png]]

# Tipos de autómatas
- [[AFD - Autómatas Finitos Deterministicos]]
- [[AFND - Autómatas Finitos No Determinísticos]]