![[Tp03 Lenguajes Regulares Automatas.pdf]]


# 1
Para saber las palabras aceptadas por los [[Autómatas Finitos]] hay que observar el recorrido del grafo generado por el conjunto de estados $Q =\{q_0, q_1, q_2, q_3\}$ . En este caso tenemos el alfabeto de entrada $\Sigma = \{0,1\}$ y el conjunto de estados finales $F = \{q_0\}$
Dibujamos el grafo que se genera dada la tabla.

```mermaid
flowchart LR;
A(((q0)))-->|0|B(q2)
A(q0)-->|1|C(q1)
C(q1)-->|0|D(q3)
C(q1)-->|1|A(q0)
B(q2)-->|0|A(q0)
B(q2)-->|1|D(q3)
D(q3)-->|0|C(q1)
D(q3)-->|1|B(q2)
```

Ejemplos posibles del diagrama:
$0101, 00,0110, 01111101$
Se puede con observacion atenta se puede ver que siempre termina teniendo un numero par de 1 y 0. Entonces el lenguaje obtenido es:
$$L= \{\omega \in \{0, 1\}^{*}: |\omega|_0 \equiv 0(2) \land |\omega|_1 \equiv 0(2) \}$$
# 2

Ver [[Autómatas Finitos Deterministicos#Minimización de un AFD]].


# 4.
