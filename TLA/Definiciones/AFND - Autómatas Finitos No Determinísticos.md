$$
A = <Q, \Sigma, q_0, F, \delta>
$$
> Un estado puede mandar a dos estados distintos con una transición.

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
Con que haya uno terminal ya puedo decir que $01 \in L(N)$

# Función de transición
> En los AFND la función de transición se define $\delta: Q \times \Sigma\rightarrow P(Q)$ donde $P(Q)$ denota todos los dubconjunots de $Q$.



