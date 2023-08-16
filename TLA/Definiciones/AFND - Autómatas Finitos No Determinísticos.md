$$
A = <Q, \Sigma, q_0, F, \delta>
$$
> Un estado puede mandar a dos estados distintos con una transición.

$$
L(AFND) = \{\omega \in \Sigma^{*} : \hat{\delta}(q_0, \omega)~ \cap~ F \ne \varnothing\}
$$
Esto sigifica la intersección del conjunto de estados finales con las unión de los posibles estados del AFND, debe ser vacío.

#### Ejemplo
| $\delta$  | 0| 1|
| -- | -- | -- |
|q0|{q0q1} | q0
|q1| - | q2 |
|q2 | -| - |
$P(q) = \{\varnothing, \{q_0\}, \{q_1\}, \{q_2\}, \{q_0, q1\}, \ldots \{q_0, q_1, q_2\}\}$

$$
[q_0, 01] \mapsto 
\begin{cases}
[q_1, 1] \mapsto [q_2, \lambda]\\
[q_0, 1] \mapsto [q_0, \lambda]
\end{cases}
$$
Con que haya uno terminal ya puedo decir que $01 \in L(AFND = N)$

# Función de transición
> En los AFND la función de transición se define $\delta: Q \times \Sigma\rightarrow P(Q)$ donde $P(Q)$ denota todos los dubconjunots de $Q$.


# Equivalencia entre [[AFD - Autómatas Finitos Deterministicos]] y AFD

- Construimos un AFD y luego buscamos la equivalencia.

> Todo lenguaje reconocido por un AFND puede ser reconocido por un AFD y viceversa.

Sea $N = <Q_N, \Sigma, \delta_N, q_0, F_N>$ y $D = <Q_D, \Sigma, \delta_0, \{q_0\}, F_D>$
donde
- $Q_D = P(Q_N)$
- $F_D = \{S \in Q_D : S~\cap~F_N \ne \varnothing\}$
- $\forall a\in \Sigma, \forall S \subseteq Q_N : \delta_D(S, a) = \cup_{p\in S}\delta_N(p, a)$
Siguiendo [[#Ejemplo]]

|$\delta_D$ | 0 | 1 |
| --  | -- | -- | 
|$q_0$ |$\{q_0, q_1\}$ | $q_0$ |
|$\{q_0, q_1\}$ |$\{q_0, q_1\} \cup \varnothing$ |$\{q_0\} \cup \{q_2\}$ |
|$*\{q_0, q_2\}$ |$\{q_1, q_2\}$ |$\{q_1\}$ |

> Partimos de q_0 y agregamos las transiciones que no pertenecen aun
> ![[Pasted image 20230816162550.png]]
> Se puede hacer una “construcción lazy” para dejar en 𝑄𝐷 sólo los estados accesibles.