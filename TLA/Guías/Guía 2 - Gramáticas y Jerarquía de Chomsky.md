Contenido
- [[#1|1]]
- [[#2|2]]
- [[#3|3]]
- [[#4|4]]
	- [[#4#$L = L(G_1)$|$L = L(G_1)$]]
	- [[#4#$L = L(G_2)$|$L = L(G_2)$]]
- [[#5|5]]
	- [[#5#$L = L(G_1)$|$L = L(G_1)$]]
	- [[#5#$L= L(G_2)$|$L= L(G_2)$]]
- [[#6|6]]
- [[#7|7]]
- [[#8|8]]
- [[#9|9]]
- [[#10|10]]
- [[#11|11]]
	- [[#11#$L_1=\{ab^{n}a, n\in \mathbb{N}\}$|$L_1=\{ab^{n}a, n\in \mathbb{N}\}$]]
		- [[#$L_1=\{ab^{n}a, n\in \mathbb{N}\}$#Libre de contexto|Libre de contexto]]
		- [[#$L_1=\{ab^{n}a, n\in \mathbb{N}\}$#Regular|Regular]]
	- [[#11#$L_2 = \{0^{n}1, n \in \mathbb{N}\}$|$L_2 = \{0^{n}1, n \in \mathbb{N}\}$]]
		- [[#$L_2 = \{0^{n}1, n \in \mathbb{N}\}$#Libre de contexto|Libre de contexto]]
		- [[#$L_2 = \{0^{n}1, n \in \mathbb{N}\}$#Regular|Regular]]
- [[#12|12]]


![[Tp02 Gramáticas.pdf]]


# 1
Sea la [[Gramática]] $G = <\{S, A, B\}, \{1, 0\}, P, S>$  y su conjunto producción $P = \{S \rightarrow 0B,S \rightarrow 1A, A \rightarrow 0, A \rightarrow 0S, A \rightarrow 1AA, B \rightarrow 1, B \rightarrow 1S, B \rightarrow 0BB \}$
El [[Lenguaje]] obtenido es aquel que tiene la misma cantidad de 0 que de 1.
$$L(G) = \{\omega \in \{1, 0\}^{+}: |\omega|_0 = |\omega|_1\}$$

# 2 
El lenguaje $L(G)$ generado por $P = \{S\rightarrow aSb | \lambda\}$ es: 
$$L(G) = \{\omega \in \{a, b\}^{+} : hay~igual~cantida~ de~a's~por~izquierda~que~de~b's~por~derecha\}$$
Que es lo mismo que
$$L(G) = \{a^{n}b^{n} : n \geq 0\}$$
# 3
Sea $G = <\{A, B\}, \{0, 1, 2\}, A, \{A\rightarrow 0B|2, B \rightarrow 0A|1\}>$
Obtener las derivaciones de 002, 0001.

$$'002' = A \rightarrow 0B \rightarrow 0(0A) \rightarrow 002$$

$$'0001' = A \rightarrow 0B \rightarrow 0(0A) \rightarrow 00(0B) \rightarrow 0001$$
Y el lenguaje que genera es 
$$L(G) = \Biggl\{ 0^{n}x: n\geq 0 ~\land~x = \begin{cases}1 & si~n~impar\\2 & caso~contrario\lor n=0 \end{cases} 
\Biggl\}$$

# 4
Para ver si dos gramáticas son equivalentes hay que ver [[Gramática#Equivalencia de gramáticas]].
$P_1 = \{S\rightarrow aSb|\lambda\}$
$P_2 = \{S\rightarrow aAb|\lambda, A\rightarrow aAb | \lambda\}$


Demostramos por inducción que ambos generan $L = \{a^{i}b^{i}: i\geq 0\}$

## $L = L(G_1)$
> $\omega \in L \Rightarrow \omega \in L(G_1)$
- **Caso base**: $i= 0 \Rightarrow \omega = \lambda$ 
	- como $S \rightarrow \lambda \in P_1 \Rightarrow \lambda \in L(G_1)$
- **Hipótesis inductiva P(n)**: $a^{n}b^{n} \in L(G_1)$ 
- **Tésis inductiva P(n+1)** $a^{n+1}b^{n+1} \in L(G_1)$
	- $S \rightarrow aSb \rightarrow \ldots \rightarrow a^{n}Sb^{n} \in L(G_1)$
	- $a^{n}Sb^{n} \rightarrow a^{n+1}Sb^{n+1}$
	- $S \rightarrow \lambda \Rightarrow S \rightarrow a^{n+1}b^{n+1} \in L(G_1)$

> $\omega \in L(G_1) \Rightarrow  \omega \in L$
- Todas las [[Gramática#Formas sentenciales]] que aún no son palabras son de la forma $a^{n}Sb^{n}$ lo único que queda para formar una palabra (sentencia) es $S\rightarrow \lambda$  $\therefore$ solo se obtienen palabras de la forma $a^{n}b^{n} \in L$ 
## $L = L(G_2)$
> $\omega \in L \Rightarrow \omega \in L(G_2)$
- **Caso base**: $i= 0 \Rightarrow \omega = \lambda$
	- $\lambda \in L_(G_2)$ pues $S \rightarrow \lambda$
- **Hipotesis**: $i = n \Rightarrow \omega = a^{n}b^{n} \in L(G_2)$
- **Tesis** : $i = n+1 \Rightarrow a^{n+1}b^{n+1} \in L(G_2)$
	-  $S\rightarrow a(A\rightarrow aAb|\lambda)b$
	- $S \rightarrow aAb \rightarrow \ldots \rightarrow aa^{n}b^{n}b = a^{n+1}b^{n+1}$

> $\omega \in L(G_2) \Rightarrow \omega \in L$
- Como en el caso anterior, todas las posibles combinaciones son del tipo $a^{n}Ab^{n}$ donde para foramr la palabra $A$ toma el valor $\lambda$ y así generando una palabra de la forma $a^{n}b^{n} \in L$


# 5
Dado $G_1 = <\{S\}, \{b\}, S, P=\{S\rightarrow bbS|bb\}>$

Para definir la gramática, tenemos que usar [[Gramática#Gramáticas tipo 3 Regulares]].
Propongo 
$$G_2 = <\{S,A\},\{b\}, S, P=\{S\rightarrow bA, A\rightarrow bS | b\}>$$
En este caso tenemos que demostrar que $L(G_1)= L(G_2) = L =\{b^{2i}:i \geq 1\}$

## $L = L(G_1)$ 
> $\forall \omega \in L \Rightarrow \omega \in L(G_1)$
- Caso base : $i = 1 \Rightarrow \omega = bb \in L(G_1)$
- Hipotesis: $i=n \Rightarrow \omega = b^{2n} \in L(G_1)$
- Tesis: $i = n+1 \Rightarrow \omega = b^{2(n+1)} \in L(G_1)$
	- Tomamos hasta nuestra hipotesis $S\rightarrow bbS \rightarrow \ldots \rightarrow (bb)^{n}S$
	- Un paso mas nos da $(bb)^{n}bb = b^{n}b^{n}b^{2} = b^{2n+2}= b^{2(n+1)} \in L(G_1)$

> $\omega \in L(G_1) \Rightarrow \omega \in L$
- Todas las palabras (solo simbolos terminales) son de la forma $(bb)^{n}$ con $n$ transformaciones. Esto es lo mismo que decir $b^{2n}$. Entonces todas las palabras formadas por $L(G_1)$ pertenecen también a $L$.

## $L= L(G_2)$
> $\forall \omega \in L \Rightarrow \omega \in L(G_2)$
- Caso base $i = 1 \Rightarrow \omega = bb$
	- $S\rightarrow bA \rightarrow bb \in L(G_2)$
- Hipotesis $i = n \Rightarrow \omega = (bb)^{n} \in L(G_2)$
- Tesis $i = n +1 \Rightarrow \omega = (bb)^{n+1} \in L(G_2)$
	- $S\rightarrow bA \rightarrow bbS \rightarrow \ldots \rightarrow (bb)^{n}S$
	- $(bb)^{n}S \rightarrow (bb)^{n}bA \rightarrow (bb)^{n}bb = (bb)^{n+1} = b^{2n+1} \in L(G_2)$

> $\omega \in L(G_2) \Rightarrow \omega \in L$

![[Pasted image 20230810122012.png]]


# 6
Dado $G = <\{S, A, B\}, \{a, b\}, S, P = \{S\rightarrow AB, A\rightarrow \lambda |aA, B \rightarrow b |bB\} >$

$$G = <\{S, A, B\}, \{a, b\}, S, P = \{ S\rightarrow aS|bB, B\rightarrow bB | \lambda\}$$
# 7
¿Los lenguajes que generan las dadas gramáticas son
[[Gramática#Clasificación de gramáticas (Jerarquía de Chomsky)#Gramáticas tipo 3 Regulares]] ?
1. $L=\{c^{i}: i\geq 0\}$
	1. $\lambda, c, cc, ccc, cccc$
	2. NO es de tipo 3 pues $A\rightarrow AA$.
2. $L=\{c^{n}d^{m}: m,n \geq 0\}$
	1. $\lambda, c, d, cd, dd, cc, ccccccd, cccccc, ddddd, cddddddd, cd$
	2. NO es de tipo 3 pues mezcla $Ad$ con $cA$.
3. $L=\{c^{i}cc^{i} = c^{2i+1}: i \geq 0\}$
	1. $c, ccc, ccccc, ccccccc$
	2. No es de tipo 3.
4. $L = \{0^{i}c0^{j} : i, j\geq 1\}$
	1. $0c0, 0000000c000, 0c0000$
	2. No es de tipo 3.

# 8

¿$P = \{S\rightarrow \lambda | aSa| bSb\} \equiv L= \{\omega = xx^{R} : x\in \{a, b\}^{*}\}$?

> $\forall \omega \in L(G) \Rightarrow  \omega \in L$
> Lo demostramos por inducción en la cantidad de pasos de derivación.
- Caso base
	- En un solo paso, se obtiene $S\rightarrow \lambda \in L$ 
- Hipotesis 
	- $S\rightarrow^{*}_{n} \omega \in L$
- Tesis
	- $S\rightarrow^{*}_{n+1} \omega \in L$
	- $S\rightarrow^{*}_{n} xx^{R} \in L$
	- El último paso para conseguir $xx^{R}$ fue $S\rightarrow \lambda$
	- $\Rightarrow S \rightarrow^{*}_{n-1} xSx^{R} \rightarrow xx^{R}$
	- Se podría haber aplicado 
		- $S\rightarrow xaSax^{R}\rightarrow xaax^{R}$
			- $(xa) = a(x)^{R} \Rightarrow ~si~ x'=xa, S\rightarrow x'x'^{R}$ es palíndromo en $\{a, b\}^{*}$
			- Esto implica que $S \Rightarrow^{*}_{n+1} \omega \in L$
		- $S\rightarrow xbSbx^{R}$
			- Análogo

> $\forall \omega \in L \Rightarrow \omega \in L(G)$
> Por inducción en la longitud de $x: \omega = xx^{R}$

- Caso base
	- $|x| = 0 \Rightarrow \omega = \lambda \in L(G)$
- Hipotesis
	- $|x| = n \Rightarrow \omega =xx^{R} \in L(G)$
- Tesis
	- $|x| = n+1 \Rightarrow \omega =xx^{R} \in L(G)$
		- Tengo que mostrar que cuando $|x| = n+1$ se puede obtener con $L(G)$
		- Sea $|x| =n\Rightarrow \omega = (x)(x)^{R}$
		- $|x| =n+1\Rightarrow x = ax'$ 
			- $\omega = (ax')(ax')^{R} = axx^{R}a$
				- Por hipótesis $xx^{R} \in L(G)$ o sea que $S\rightarrow^{*} x'x'^{R}$
				- $\Rightarrow S\rightarrow^{*} a(x'x'^{R})a$
			- $\omega = (xb)(xb)^{R} = xbbx$
				- Análogo
![[Pasted image 20230810140236.png]]

# 9
Las producciones que impiden que sea una gramática de tipo 3 son:
- $S\rightarrow 21$
- $A2\rightarrow *$
- $B\rightarrow A1$
- $C\rightarrow A0$
- $C\rightarrow 10$
- Quedaría $\{S\rightarrow 1B|0A|\lambda, B\rightarrow 0B|1|\lambda, C\rightarrow 0|2B|1C\}$
- Y obviamente no se obtiene la misma gramática pues se puede intentar conseguir la palabra '21' pero es imposible. 
o en el caso de gramática lineal por izquierda
- $S\rightarrow 21$
- $S\rightarrow 1B | 0A$
- $A2\rightarrow *$
- $B\rightarrow 0B | 0A$
- $C\rightarrow 2B | 1C |10$


# 10
$\omega \in L(G_1): \{000001, 0011111\}$
$\omega \in L(G_2): \{0111111, 0011111\}$
Generan las mismas palabras.

# 11


## $L_1=\{ab^{n}a, n\in \mathbb{N}\}$
Recordar [[Gramática#Gramáticas tipo 2 Libres de contexto]].
Considerando que $\min\{\mathbb{N}\} = 1$


### Libre de contexto
$$P_{2_1} = \{S\rightarrow abBa, B\rightarrow \lambda| bB\}$$
### Regular

$$P_{3_1} = \{S\rightarrow aB,B \rightarrow bB|bC, C\rightarrow a\}$$
## $L_2 = \{0^{n}1, n \in \mathbb{N}\}$

### Libre de contexto
$$P_{2_2} = \{S\rightarrow 0A1, A\rightarrow 0A | 0\}$$

### Regular
$$P_{3_2} = \{S\rightarrow 0A, A\rightarrow 0A | 1\}$$

# 12
$G =<\{a, b, c\},\{A, B, C\},S = A, P =\{A\rightarrow B|BC, B\rightarrow aB|Bc|bC, C\rightarrow ab|bc|\lambda\}>$
Demostrar que la las siguientes palabras están en $L(G)$. Para esto vamos a obtener la derivación de los mismos mediantes las formas sentenciales generadas por el lenguaje de la gramática.
- $aabbc$
	- $A \rightarrow B \rightarrow aB\rightarrow a(aB) \rightarrow aa(bC)\rightarrow aabbc \in L(G)$
- $ababc$
	- $A \rightarrow B \rightarrow aB\rightarrow a(Bc) \rightarrow a(bC)c \rightarrow ab(ab)c \in L(G)$
- $abab$
	- $A \rightarrow BC \rightarrow (aB)(ab)\rightarrow a(bC)ab \rightarrow ab(\lambda)ab\rightarrow abab \in L(G)$
