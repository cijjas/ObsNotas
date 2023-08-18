![[Tp03 Lenguajes Regulares Automatas.pdf]]


# 1
Para saber las palabras aceptadas por los [[Autómatas Finitos]] hay que observar el recorrido del grafo generado por el conjunto de estados $Q =\{q_0, q_1, q_2, q_3\}$ . En este caso tenemos el alfabeto de entrada $\Sigma = \{0,1\}$ y el conjunto de estados finales $F = \{q_0\}$
Dibujamos el grafo que se genera dada la tabla.

```mermaid
flowchart LR;
A(((q0)))-->|0|B
A-->|1|C
C((q1))-->|0|D
C-->|1|A
B((q2))-->|0|A
B-->|1|D
D((q3))-->|0|C
D-->|1|B
```

Ejemplos posibles del diagrama:
$0101, 00,0110, 01111101$
Se puede con observacion atenta se puede ver que siempre termina teniendo un numero par de 1 y 0. Entonces el lenguaje obtenido es:
$$L= \{\omega \in \{0, 1\}^{*}: |\omega|_0 \equiv 0(2) \land |\omega|_1 \equiv 0(2) \}$$
# 2

## A
Ver [[AFD - Autómatas Finitos Deterministicos#Minimización de un AFD]].

```mermaid
flowchart LR;
A((p))-->|a|B
A-->|b|A
B(((q)))-->|a|C
B-->|b|D
C(((r)))-->|a|B
C-->|b|E
D((s))-->|a|E
D-->|b|F
E((t))-->|a|D
E-->|b|F
F((u))-->|a|B
F-->|b|F
```

$$\frac{Q}{E_0}= \{F, Q-F\} = \{\{q, r\}, \{p,s,t,u\}\}$$
Ahora tengo que ver dentro de cada clase cuales de los pares producen una una cadena dentro de la misma clase.
Por ejemplo:

$\delta(q, a) = r \in C_1 ~~~~~~~~ \delta(q, b) = s \in C_2$
$\delta(r, a) = q \in C_1 ~~~~~~~~ \delta(r, b) = t \in C_2$

Por otro lado analizando $C_2$
$\delta(p, a) = q \in C_1 ~~~~~~~~ \delta(p, b) = p \in C_2$
$\delta(s, a) = t \in C_2 ~~~~~~~~ \delta(s, b) = u \in C_2$
$\delta(t, a) = s \in C_2 ~~~~~~~~ \delta(t, b) = u \in C_2$
$\delta(u, a) = q \in C_1 ~~~~~~~~ \delta(u, b) = u \in C_2$

Vemos que no nos lleva a la misma clase
$\Rightarrow \{C_1= \{q, r\} ,C_2 = \{s,t\}, C_3= \{p,u\}\}$

Nos queda que 
$\delta(s, a) = t \in C_2 ~~~~~~~~ \delta(s, b) = u \in C_3$
$\delta(t, a) = s \in C_2 ~~~~~~~~ \delta(t, b) = u \in C_3$
y
$\delta(p, a) = q \in C_1 ~~~~~~~~ \delta(p, b) = p \in C_3$
$\delta(u, a) = q \in C_1 ~~~~~~~~ \delta(u, b) = u \in C_3$

De esto podemos graficar, obtener el Autómata Mínimo y hacer la tabla
$$A = <\{P,Q,R\},\{a,b\}, \delta, P, R>$$
```mermaid
flowchart LR;
A(((R)))-->|a|A
A-->|b|B
B((Q))-->|a|B
B-->|b|C
*-->C
C(P)-->|a|A
C-->|b|C
```

| $\delta$ | a |  b|
|-------------|-| - |
|$P$ |$R$ |$P$ |
|$Q$ |$Q$ |$P$|
|$R$ | $R$| $Q$|


## B

$$\frac{Q}{E_0} = \{\{q_3,q_4,q_5\}, \{\bar{q_0}, q_1, q_2\}\}$$

$$
C_2:
\begin{cases}
	\delta(q_0, 0) = q_1 \in C_2 ~~~~ \delta(q_0, 1) = q_2 \in C_2\\
	\delta(q_1, 0) = q_2 \in C_2 ~~~~  \delta(q_1, 1) = q_3 \in C_1\\
	\delta(q_2, 0) = q_2 \in C_2 ~~~~ \delta(q_2, 1) = q_4 \in C_1\end{cases}
$$
$$
C_1:
\begin{cases}
	\delta(q_3, 0) = q_3 \in C_1 ~~~~ \delta(q_3, 1) = q_3 \in C_1\\
	\delta(q_4, 0) = q_4 \in C_1 ~~~~ \delta(q_4, 1) = q_4 \in C_1\\
	\delta(q_5, 0) = q_5 \in C_1 ~~~~ \delta(q_5, 1) = q_4 \in C_1
\end{cases}
$$
Vemos que en $C_2$ vamos a dividir en dos clases distintas $C_2$ y $C_3$
$$\frac{Q}{E_1} = \{\underbrace{\{q_3, q_4, q_5\}}_{C_1=q_1},\underbrace{ \{q_1,q_2\}}_{C_2 = q_2}, \underbrace{\{\bar{q_0}\}}_{C_3 = q_0}\}$$
$$
C_2:
\begin{cases}
	\delta(q_1, 0) = q_2 \in C_2 ~~~~  \delta(q_1, 1) = q_3 \in C_1\\
	\delta(q_2, 0) = q_2 \in C_2 ~~~~ \delta(q_2, 1) = q_4 \in C_1
\end{cases}
$$
$$
C_3 : 
\begin{cases}\delta(q_0, 0) = q_1 \in C_2 ~~~~ \delta(q_0, 1) = q_2 \in C_2
\end{cases}
$$

$$
C_1:
\begin{cases}
	\delta(q_3, 0) = q_3 \in C_1 ~~~~ \delta(q_3, 1) = q_3 \in C_1\\
	\delta(q_4, 0) = q_4 \in C_1 ~~~~ \delta(q_4, 1) = q_4 \in C_1\\
	\delta(q_5, 0) = q_5 \in C_1 ~~~~ \delta(q_5, 1) = q_4 \in C_1
\end{cases}
$$

Luego ya no hay elementos de las clases que vayan a elementos diferentes que no pertenecen a la clase propia, entonces finalizamos.
```mermaid
stateDiagram-v2
direction LR
[*] --> q0
q0 --> q2 : 1,0
q2 --> q2 : 0
q2 --> q1 : 1
q1 --> q1 : 1,0
q1 --> [*]
```

## C

$$\frac{Q}{E_0} = \{q_5, \{q_0, \ldots, q_4\}\}$$
$$
C_2\begin{cases}
\delta(q_0, a) = q_1 \in C_2 ~~~~~~~~  \delta(q_0, b) = q_2 \in C_2\\
\delta(q_1, a) = q_3 \in C_2 ~~~~~~~~  \delta(q_1, b) = q_4 \in C_2\\
\delta(q_2, a) = q_4 \in C_2 ~~~~~~~~  \delta(q_2, b) = q_3 \in C_2\\
\begin{rcases}
	\delta(q_3, a) = q_5 \in C_1 &&  \delta(q_3, b)= q_4 \in C_2 \\
	\delta(q_4, a) = q_5 \in C_1 &&  \delta(q_4, b) = q_3 \in C_2\\
\end{rcases} ~diferentes
\end{cases}
$$

Continuo separando
$$\frac{Q}{E_1} = \{q_5, \{q_0, q_1, q_2\}, \{q_3, q_4\}\}$$

$$
C_2\begin{cases}
\delta(q_0, a) = q_1 \in C_2 &&  \delta(q_0, b) = q_2 \in C_2\\
\delta(q_1, a) = q_3 \in C_3 &&  \delta(q_1, b) = q_4 \in C_3\\
\delta(q_2, a) = q_4 \in C_3 &&  \delta(q_2, b) = q_3 \in C_3\\
\end{cases}
$$

$$
C_3
\begin{cases}
	\delta(q_3, a) = q_5 \in C_1 &&  \delta(q_3, b)= q_4 \in C_3 \\
	\delta(q_4, a) = q_5 \in C_1 &&  \delta(q_4, b) = q_3 \in C_3\\
\end{cases}
$$

Vuelvo a separar pues en $C_2$ tenemos elementos que van a diferentes clases:
$$\frac{Q}{E_2} 
= \{
\underbrace{q_5 }_{C_1 = p},
\underbrace{q_0 }_{C_2 = q},
\underbrace{\{q_1, q_2\} }_{C_3 = r},
\underbrace{\{q_3, q_4\}}_{C_4 = s}\}
$$
Y acá ya queda bien definido. Luego nos queda:
```mermaid
stateDiagram-v2
direction LR
[*] --> q
p --> [*]
p --> p : a, b
q --> r : a, b
r --> s : a, b
s --> p : a
s --> s : b
```

# 3
## A
Palabras donde b es precedido inmediatamente por a.

```mermaid
stateDiagram-v2
direction LR
[*] --> p
p --> p : a
p --> q : b
q --> p : a
p --> [*]
```


## B
$n \in \mathbb{N} : n \equiv 0(3)$
por ejemplo 4->3
- Estado 0 : multiplo de 3
- Estado 1 : módulo 1 
- Estado 2 : módulo 2

```mermaid
stateDiagram-v2
direction LR
[*] --> X
X --> N : 0
X --> E0 : 3, 6, 9
E0 --> E0 : 0,3, 6, 9
E0 --> E1 : 2, 5, 8
E0 --> E2 : 1, 4, 7
E0 --> [*]
X --> E1 : 2, 5, 8
E1 --> E0 : 1, 4, 7
E1 --> E1 : 2, 5, 8
E1 --> E2 : 0,3, 6, 9
X --> E2 : 1, 4, 7
E2 --> E0 : 2, 5, 8
E2 --> E1 : 0,3, 6, 9
E2 --> E2 : 1, 4, 7
```


## C
Palabras que no tengan $abaab$

```mermaid
stateDiagram
direction LR
[*] --> p
p --> q : a
p --> p : b
q --> q : a 
q --> r : b
r --> p : b
r --> s : a
s --> r : b
s --> t : a
t --> q : a
```

## D
Palabras que no tengan más de 3 a's

```mermaid
stateDiagram 
direction LR
[*] --> p
p --> q : a
p --> p : b
q --> r : a
q --> q : b
r --> r : b
r --> s : a
s --> s : b
p --> [*]
q --> [*]
r --> [*]
s --> [*]

```
## E
$L = \{x:x\in\{1, 2, 3\}^{*} \land |x| \gt 0\}$
Y sea $x = x_0x_1\ldots x_n2 \Rightarrow (\sum_{i = 0}^nx_i) + 2\equiv 0(3) \qquad n \geq 1$

Hay que separar los estados posibles
- Nietzsche: Estado 0 : la suma es $(\sum_{i = 0}^nx_i) + 2 = 0\mod(3)$
	- Suma 1 : se mueve al estado 1
	- Suma 2 : se mueve al estado 2
	- Suma 3 : se mueve al estado 0
- Ingenieros: Estado 1 : la suma es $(\sum_{i = 0}^nx_i) + 2 = 1\mod(3)$
	- Suma 1 : se mueve al estado 2
	- Suma 2 : se mueve al estado 0
	- Suma 3 : se mueve al estado 1
- Tesla :Estado 2 : la suma es $(\sum_{i = 0}^nx_i) + 2 = 2\mod(3)$
	- Suma 1 : se mueve al estado 0
	- Suma 2 : se mueve al estado 1
	- Suma 3 : se mueve al estado 2

Desde un inicio se puede decir que se encuentra en el **estado 1** pues el 2 está asegurado. El unico nodo de aceptación va a ser el de estado 0 ya que este es el que me dice que es multiplo de 3.
```mermaid
stateDiagram
direction LR
[*] --> X 
X --> Nietzsche: 1
Nietzsche --> Ingenieros : 1
Nietzsche --> Tesla : 2
Nietzsche --> Nietzsche : 3
X --> Ingenieros : 2
Ingenieros --> Tesla : 1
Ingenieros --> Nietzsche : 2
Ingenieros --> Ingenieros : 3
X --> Tesla : 3
Tesla --> Nietzsche : 1
Tesla --> Ingenieros : 2
Tesla --> Tesla : 3
Nietzsche --> [*] : 2
```

# 4
> Se cuenta con una canilla y dos jarras, una tiene una capacidad de 4 litros y la otra es de 3 litros.

¿Es posible obtener 2 litros de agua en una de las jarras? Modelar el problema con un AFD y escribir una secuencia de configuraciones que lleve a la solución.

$B1 :$ botella de 3 litros
$B2 :$ botella de 4 litros

- Estado 0 : botellas vacias.
- Estado 1 : botella de 3 litros llena y la de 4 vacia.
- Estado 2 : botella de 3 litros vacia y la de 4 llena.
- Estado 3 : botella de 3 litros llena y la de 4 llena.
- Estado 4 : botella de 4 litros con 3 litros y la de 3 litros vacia
- Estado 5 : B1 y B2 con 3 litros
- Estado 6 : 4 litros en B2 y 2 litros en B1
- Estado A : botella con 2 litros

```mermaid
stateDiagram
[*] --> 0
0 --> 1 : Llenamos B1
1 --> 4 : Vertimos B1 en B2
4 --> 5 : Llenamos B1
5 --> 6 : Vertimos 1 litro de B1 en B2
0 --> 2 : Llenamos B2
2 --> 3B : Vertimos 3 
0 --> 3
6 --> [*]
```

# 5
$$
\{\{s, t, u, v\}, \{p,q,r\}\}
$$
$$
\begin{cases}
\delta(s, a) = q \in C_2 & \delta(s, b) = t \in C_1& \delta(p, c) = u \in C_1\\
\delta(t, a) = t \in C_1 & \delta(t, b) = v \in C_1& \delta(t, c) = u \in C_1\\
\delta(u, a) = t \in C_1 & \delta(u, b) = t \in C_1 & \delta(
u, c) = v \in C_1\\
\delta(v, a) = u \in C_1 & \delta(v, b) = u \in C_1 & \delta(v, c) = t \in C_1\\
\end{cases}
$$
$$
\begin{cases}
\delta(p, a) = r \in C_2 & \delta(p, b) = t \in C_1& \delta(p, c) = q \in C_2\\
\delta(q, a) = q \in C_2 & \delta(q, b) = v \in C_1& \delta(q, c) = p \in C_2\\
\delta(r, a) = p \in C_2 & \delta(r, b) = u \in C_1 & \delta(r, c) = r \in C_2\\
\end{cases}
$$

Separo las que son de clases diferentes
$$
\Rightarrow 
\begin{cases}
\delta(t, a) = t \in C_1 & \delta(t, b) = v \in C_1& \delta(t, c) = u \in C_1\\
\delta(u, a) = t \in C_1 & \delta(u, b) = t \in C_1 & \delta(
u, c) = v \in C_1\\
\delta(v, a) = u \in C_1 & \delta(v, b) = u \in C_1 & \delta(v, c) = t \in C_1\\
\end{cases}
$$
$$
\begin{cases}
\delta(s, a) = q \in C_2 & \delta(p, b) = t \in C_1& \delta(p, c) = u \in C_1\\
\end{cases}
$$
```mermaid
stateDiagram
direction LR
[*] --> q
q --> q : a, c
q --> p : b
p --> p : a, b,c
r --> q : a
r --> p : a ,c
r --> [*]
p --> [*]

```
Luego minimizando $A_2$

$$
\{\{p, q\}, \{r, s, t\}\}
$$
$$
\begin{cases}
	\delta(p, a) = s \in C_2 & \delta(p, b) = q \in C_1 & \delta(p, c) = p \in C_1\\
	\delta(q, a) = t \in C_2 & \delta(q, b) = p \in C_1 & \delta(q, c) = q \in C_1\\
\end{cases}
$$
$$
\begin{cases}
	\delta(r, a) = q \in C_1 & \delta(r, b) = t \in C_2 & \delta(r, c) = s \in C_2\\
	\delta(s, a) = s \in C_2 & \delta(s, b) = t \in C_2 & \delta(s, c) = s \in C_2\\
	\delta(t, a) = t \in C_2 & \delta(t, b) = s \in C_2 & \delta(t, c) = s \in C_2\\
	
\end{cases}
$$
Separo $\{\{p, q\},  \{s, t\},\{r\}\}$

$$
\begin{cases}
	\delta(r, a) = q \in C_1 & \delta(r, b) = t \in C_2 & \delta(r, c) = s \in C_2\\
\end{cases}
$$


Luego 
```mermaid
stateDiagram
direction LR
[*] --> p
p --> q : a
p --> p : b, c
q --> q : a, b, c
r --> p : a
r --> q : b, c
r --> [*]
q --> [*]
```
Si miramos con atención vemos que no son el mismo diagrama de estados.


#ParcialTLA
El estado $\varnothing$ existe en los estados no terminales (es el estado al que van las cosas si está vacío el slot en la tabla)
# 6
$$L = \{a^{n}:n\geq 0\} \cup \{b^{n}a:n\geq 1\}$$
Este lenguaje genera por ejemplo las palabras:
- ba
- aba
- aabba
- aaba
- aaaaaaaaabbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbba

```mermaid
stateDiagram
direction LR
[*] --> p
p --> q : a
p --> r : b
r --> s : a
r --> r : b
s --> [*]
q --> q : a
q --> t : b
t --> t : b
t --> u : a
u --> [*]
```
Este autómata es $A = <\{a, b\}, \{p, q, r,s, t, u\}, \delta, p, \{s, u\}>$

# 7

## a
#### Primera forma práctica
Para arrancar, calculo las clausuras de los elementos
$$
\begin{cases}
clausura(q_0) = \{q_0\}\\
clausura(q_1) = \{q_1, q_2\}\\
clausura(q_2) = \{q_2\}
\end{cases}
$$
Hago la tabla con $\lambda$  donde hago todos los posibles alcances a distancia de un único paso sin incluirse a sí mismos. Aquel estado que no tenga una transición completa se le asigna la transición a un estado trampa $T$. En las transiciones de lambda no pongo $T$ pues no existe esa transición.

| $\delta$ | $\lambda$  | $0$ | $1$|
| -- | --  | -- | -- |
| $\rightarrow q_0$ |   | $\{q_1\}$ | $\{q_1\}$ |
| $*q_1$ | $\{q_2\}$  | $\{q_0, q_2\}$ | $\{q_1\}$ |
| $q_2$ |   | $T$ | $\{q_1\}$ |
| $T$ |   | $T$ | $T$ |

Luego, hago otra tabla sin $\lambda$ en la que anoto todas las transiciones posibles de longitud uno, tomando en cuenta que $\lambda$ no consume. Recordar que si se está parado en un estado, las conexiones $\lambda$ permiten que sea equivalente estar parado en el siguiente estado.
![[Pasted image 20230817183642.png]]
Entonces nos queda la tabla

| $\delta$ | $0 = \lambda(\delta(q_i, 0))$| $1 = \lambda(\delta(q_i, 1))$ |
| -- | --- | --|
| $q_0$ | $q_1, q_2$ | $q_1, q_2$ |
| $q_1$ | $q_0, q_2$ | $q_1, q_2$ |
| $q_2$ | $T$ | $q_1, q_2$ |
| $T$ | $T$ | $T$ |

Luego esta tabla la pasaremos a DFA. Comenzando en la primera celda con $\lambda(q_0)$


|$\delta$ | $0$| $1$  |  
| -- | -- | -- |
| $q_0 : A$ | $\{q_1, q_2\} \cup \varnothing :B$ | $\{q_1, q_2\} \cup \varnothing : B$| 
|$\{q_1, q_2\}\cup \varnothing :B$ | $\{q_0, q_2\}: C$ | $\{q_1, q_2\} :B$|
|$\{q_0, q_2\} : C$ | $\{q_1, q_2\} :B$| $\{q_1, q_2\}:B$ |


#### Segunda forma medio fea (youtube)
Para arrancar, calculo las clausuras de los elementos

$$
\begin{cases}
clausura(q_0) = \{q_0\}\\
clausura(q_1) = \{q_1, q_2\}\\
clausura(q_2) = \{q_2\}
\end{cases}
$$
Hago la tabla con $\lambda$

| $\delta$ | $\lambda$  | $0$ | $1$|
| -- | --  | -- | -- |
| $\rightarrow q_0$ | $\{q_0\}$  | $\{q_1\}$ | $\{q_1\}$ |
| $*q_1$ | $\{q_1, q_2\}$  | $\{q_0, q_2\}$ | $\{q_1\}$ |
| $q_2$ | $\{q_2\}$  | $\varnothing$ | $\{q_1\}$ |

Luego hago la tabla sin $\lambda$

| $\delta$ | $0$ |  $1$ |
| -- | -- | -- |
|$\rightarrow \{q_0\} : A$ | $\{q_1\} : B$ | $\{q_1\} :B$|
|$*\{q_1\} : B$ | $\{q_0, q_2 \} : C$ | $\{q_1\} :B$|
| $\{q_0, q_2\} : C$ | $\{q_1\} :B$| $\{q_1\} : B$|

Finalmente vemos que sea minimal. Como podemos observar 
$$
\frac{Q}{E_0} = \{\{A,C\}, \{B\}\} 
$$
Luego este no es minimal por ende separo nuvamente

$$
A =\begin{cases}
\delta(A, 0) \in C_2 & \delta(A, 1) \in C_2\\
\delta(C, 0) \in C_2 & \delta(C, 1) \in C_2\\
\end{cases}
$$
$$
B = \begin{cases}
\delta(B, 0) \in C_1 & \delta(B, 1) \in C_2\\
\end{cases}
$$


```mermaid
stateDiagram
direction LR
[*] --> A
A --> B : 0, 1
B --> B : 1
B --> A : 0
B --> [*]
```


## b

La tabla pura del dibujo es:

| $\delta$ |  $0$ |  $1$ |
| -- | -- | -- |
| $\rightarrow q_0$| $\{q_0, q_1\}$|$\{q_1\}$ | 
| $*q_1$| $\{q_2\}$|$\{q_2\}$ | 
| $q_2$| $T$|$\{q_2\}$ | 

Hago las transiciones del AFD

| $\delta$ |  $0$ |  $1$ |
| -- | -- | -- |
| $\rightarrow q_0 : A$| $\{q_0, q_1\} : B$|$\{q_1\}:C$ | 
| $*\{q_0, q_1\}: B$| $\{q_0, q_1, q_2\} :D$|$\{q_1, q_2\}:E$ | 
| $*\{q_0, q_1, q_2\}:D$| $\{q_0, q_1, q_2\}:D$|$\{q_1,q_2\}:E$ | 
| $*\{q_1, q_2\}:E$| $\{q_2\}:F$|$\{q_2\}:F$ |
| $\{q_2\}:F$| $T$|$\{q_2\}:F$ | 
| $*\{q_1\}:C$| $\{q_2\}:F$|$\{q_2\}:F$ | 
| $T$| $T$|$T$ | 

$$
\frac{Q}{E_0} = \{\{C,B,D,E\}, \{A,F, T\}\}
$$
$$
\begin{cases}
\delta(C, 0) = F \in C_2 & \delta (C, 1) = F \in C_2\\
\delta(B, 0) = D \in C_1 & \delta (B, 1) = E \in C_1\\
\delta(D, 0) = D \in C_1 & \delta (D, 1) = E \in C_1\\
\delta(E, 0) = F \in C_2 & \delta (E, 1) = F \in C_2\\\\
\delta(A, 0) = B \in C_1 & \delta (A, 1) = C \in C_1\\
\delta(F, 0) = T \in C_2 & \delta (F, 1) = F \in C_2\\
\delta(T, 0) = T \in C_2 & \delta (T, 1)  = T \in C_2
\end{cases}~~~ \Rightarrow \{\{B,D\}, \{C,E\}, \{A\},\{F,T\}\}
$$
$$
\Rightarrow 
\begin{cases}
\delta(B, 0) = D \in C_1 & \delta (B, 1) = E \in C_2\\
\delta(D, 0) = D \in C_1 & \delta (D, 1) = E \in C_2\\\\
\delta(C, 0) = F \in C_4 & \delta (C, 1) = F \in C_4\\
\delta(E, 0) = F \in C_4 & \delta (E, 1) = F \in C_4\\\\
\delta(A, 0) = B \in C_1 & \delta (A, 1) = C \in C_1\\\\
\delta(F, 0) = T \in C_4 & \delta (F, 1) = F \in C_4\\
\delta(T, 0) = T \in C_4 & \delta (T, 1)  = T \in C_4
\end{cases}
$$


```mermaid
stateDiagram
direction LR
[*] --> A
A --> BD : 0
A --> CE : 1
BD --> BD : 0
BD --> CE : 1
CE --> FT : 0, 1
FT --> FT : 0, 1
CE --> [*]
BD --> [*]
```



## c

1. Clausuras

$$
\begin{cases}
clausura(q_0) = \{q_0\} \cup \{ q_2, q_3\}\\
clausura(q_1) = \{q_1\} \cup \varnothing\\
clausura(q_2) = \{q_2 \} \cup \{q_3\}\\
clausura(q_3) = \{ q_3\}\cup \varnothing\\
\end{cases}
$$

2. Tabla con $\lambda$

| $\delta$ |  $\lambda$|  $0$ | $1$ |
| -- | -- | -- | -- | 
| $q_0$ | $\{q_2, q_3\}$| $T$ | $\{q_1, q_2\}$ |
| $q_1$ | | $\{q_0\}$ | $\{q_0, q_1\}$ |
| $q_2$ | $\{q_3\}$ | $\{q_2\}$ | $T$ |
| $q_3$ |  | $T$ | $T$ |

3. Tabla sin $\lambda$

| $\delta$  | $0$ |  $1$ |
| --  |  -- |  -- |
| $\rightarrow \{q_0\}\cup \{q_2, q_3\} :A$ | $\{q_2\}\cup \{q_3\} :B$ | $\{q_1, q_2\} \cup \{q_3\} :C$ |
| $\{q_2\}\cup \{q_3\} :B$ | $\{q_2\}\cup\{q_3\}: B$|  $T$|
| $*\{q_1, q_2\} \cup \{q_3\} :C$ | $\{q_0, q_2\} \cup \{q_3\}: D$| $\{q_0, q_1\} \cup \{q_2, q_3\}:E$|
| $\{q_0, q_2\} \cup \{q_3\}: D$ | $\{q_2\} \cup \{q_3\} : B$| $\{q_1, q_2\} \cup \{q_3\} : C$|
| $*\{q_0, q_1\} \cup \{q_2, q_3\}:E$ | $\{q_0\} \cup \{q_2, q_3\} :A$| $\{q_0, q_1, q_2\} \cup \{q_3\} : E$|

4. Minimización

$$
\frac{Q}{E_0} = \{\{C,E\}, \{A, B,D, T\}\}
$$
$$
\begin{cases}
\delta(A, 0) = B \in C_2 && \delta(A, 1) = C \in C_1\\
\delta(B, 0) = B \in C_2 && \delta(B, 1) = T \in C_2\\
\delta(T, 0) = T \in C_2 && \delta(E, 1) = T \in C_2\\
\delta(D, 0) = B \in C_2 && \delta(D, 1) = C \in C_1\\\\
\delta(C, 0) = D \in C_2 && \delta(C, 1) = E \in C_1\\
\delta(E, 0) = A \in C_2 && \delta(E, 1) = E \in C_1\\
\end{cases}
$$

Divido
$$
\frac{Q}{E_0} = \{\{C, E\}, \{B, T\}, \{A, D\}\}
$$
$$
\begin{cases}
\delta(C, 0) = D \in C_3 && \delta(C, 1) = E \in C_1\\
\delta(E, 0) = A \in C_3 && \delta(E, 1) = E \in C_1\\\\
\delta(B, 0) = B \in C_2 && \delta(B, 1) = T \in C_2\\
\delta(T, 0) = T \in C_2 && \delta(E, 1) = T \in C_2\\\\
\delta(A, 0) = B \in C_2 && \delta(A, 1) = C \in C_1\\
\delta(D, 0) = B \in C_2 && \delta(D, 1) = C \in C_1\\\\
\end{cases}
$$
```mermaid
stateDiagram
direction LR
[*] --> AD
AD --> BT : 0
AD --> CE : 1
CE --> AD : 0
CE --> CE : 1
BT --> BT : 0, 1
CE --> [*]
```



# 8
Obviamente no son equivalentes pues $A_b$ aceota la palabra $a$ pero $A_a$ no. De todas formas, procedemos a la demostración en donde los AFD no son equivalentes.

Para determinar si son equivalente los transformo a AFD minimos y me fijo si son el mismo.
$$
\begin{cases}
\lambda(q_0) = \{q_0\} \cup \{q_1, q_2\}\\
\lambda(q_1) = \{q_1\} \cup \{ q_2\}\\
\lambda(q_2) = \{q_2\} \cup \{ q_1\}\\
\lambda(q_3) = \{q_3\} \cup \varnothing
\end{cases}
$$
## 1
|  $\delta$| $\lambda$  | $a$  | $b$ | 
| -- | -- | -- | --|
| $*\rightarrow q_0$ | $q_1, q_2$ | $T$| $T$|
| $q_1$ | $q_2$ | $q_3$| $T$|
| $*q_2$ | $q_1$ | $T$| $T$|
| $q_3$ |  | $q_3$| $q_2$|

|  $\delta$| $\lambda$  | $a$  | $b$ | 
| -- | -- | -- | --|
| $*\rightarrow p$ |  | $p,q$| $T$|
| $q$ |  | $q$| $r$|
| $*r$ |  | $q$| $T$|
| $s$ | $r$ | $s$| $r$|

## 2
|$\delta$  | $a$ | $b$|
| -- | -- | -- |
| $*\rightarrow q_0, q_1, q_2 :A$ | $q_3 :B$| $T$ |
| $q_3 :B$ | $q_3:B$| $q_1, q_2:C$ |
| $*q_1, q_2 :C$ | $q_3:B$| $T$ |


|$\delta$  | $a$ | $b$|
| -- | -- | -- |
| $*\rightarrow p :A$ | $p,q :B$| $T$ |
| $*p,q :B$ | $p, q:B$| $r:C$ |
| $*r :C$ | $q:D$| $T$ |
| $q :D$ | $q:D$| $r:C$ |



$$
\begin{cases}
\frac{Q_1}{E_0} = \{\{A, C\}, \{B, T\}\}\\
\frac{Q_2}{E_0} = \{\{A,B, C\}, \{ D, T\}\}\\

\end{cases}
$$

$$
Q_1:\begin{cases}
\delta(A, a) = B \in C_2 && \delta(A, b) = T \in C_2\\
\delta(C, a) = B \in C_2 && \delta(C, b) = T \in C_2\\\\
\delta(B, a) = B \in C_2 && \delta(C, b) = C \in C_1\\
\delta(T, a) = T \in C_2 && \delta(T, b) = T \in C_2\\
\end{cases}
$$
$$
Q_2:\begin{cases}
\delta(A, a) = B \in C_1 && \delta(A, b) = T \in C_2\\
\delta(B, a) = B \in C_1 && \delta(B, b) = C \in C_1\\
\delta(C, a) = D \in C_2 && \delta(C, b) = T \in C_2\\\\
\delta(D, a) = D \in C_2 && \delta(D, b) = C \in C_1\\
\delta(T, a) = T \in C_2 && \delta(T, b) = T \in C_2\\
\end{cases}
$$

Luego $\frac{Q_1}{E_1} =\{\{A, C\}, \{B\}, \{T\}\}$ y $\frac{Q_2}{E_1} = \{\{A\}, \{B\}, \{C\}, \{D\}, \{T\}\}$ 

$$
Q_1:\begin{cases}
\delta(A, a) = B \in C_2 && \delta(X, b) = T \in C_3\\
\delta(C, a) = B \in C_2 && \delta(C, b) = T \in C_3\\\\
\delta(B, a) = B \in C_2 && \delta(C, b) = C \in C_1\\\\
\delta(T, a) = T \in C_3 && \delta(T, b) = T \in C_3\\
\end{cases}
$$
$$
Q_2:\begin{cases}
\delta(A, a) = B \in C_2 && \delta(A, b) = T \in C_5\\\\
\delta(B, a) = B \in C_2 && \delta(B, b) = C \in C_3\\\\
\delta(C, a) = D \in C_4 && \delta(C, b) = T \in C_5\\\\
\delta(D, a) = D \in C_4 && \delta(D, b) = C \in C_3\\\\
\delta(T, a) = T \in C_5 && \delta(T, b) = T \in C_5
\end{cases}
$$
## 3
```mermaid
stateDiagram
direction LR
[*] --> AC 
AC --> B : a
AC --> T : b
B --> B : a
B --> AC : b
T --> T :a, b
AC --> [*]
```

```mermaid
stateDiagram
direction LR
[*] --> A
A --> B : a
A --> T : b
B --> B : a
B --> C : b
C --> D : a
C --> T : b
D --> D : a
D --> C : b
T --> T : a, b
A --> [*]
B --> [*]
C --> [*]

```
