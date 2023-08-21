Tiene sentido mirar [[Presentaciones y Material#1. Introducción]]

# Contenido

- [[#1|1]]
- [[#2|2]]
- [[#3|3]]
- [[#4|4]]
- [[#5|5]]
- [[#6|6]]
- [[#7|7]]
- [[#8|8]]
				- [[#Demostración]]
- [[#9|9]]
- [[#10|10]]
- [[#11|11]]
- [[#12|12]]
- [[#Adicional|Adicional]]
	- [[#Adicional#1|1]]

![[Tp01 Introduccion.pdf]]

# 1
Este ej sale con [[Alfabeto#Potencias de un alfabeto]]
1. Sea Σ={a,b} un alfabeto donde \#x indica la cantidad de elementos del conjunto x
	1. Hallar: Σ0, Σ1, Σ+, Σ∗ 
		1. $\Sigma ^{0} = \lambda$
		2. $\Sigma^{1} = \{a, b\}$
		3. $\Sigma ^{+} = \{a, b, aa, ab, bb, ba, \ldots\}$
		4. $\Sigma ^{+} = \{\lambda, a, b, aa, ab, bb, ba, \ldots\}$
	2. Hallar \#Σ0, \#Σ2 
		1. $\# \Sigma ^{0} = 1$
		2. $\# \Sigma ^{2} = 2^{2}$
	3. ¿cuántas palabras de longitud 3 hay en Σ∗? y de longitud k?
		1. hay $2^{3}$ palabras de longitud 3 pues por cada posible caracter de la palabra hay 2 posibilidades. Luego para una longitud $k$ hay $2^{k}$ palabras.
	4. si Σ tuviera p símbolos, ¿cuántas palabras de longitud k habría en Σ∗?
		1. $\# \Sigma  = p \Rightarrow \# \omega = p^{k}$  se puede decir que $(\# \Sigma)^{|k|}$


# 2
> Dado Σ = {a, b}, ¿cuál de las siguientes afirmaciones es verdadera y cuál falsa?
- $\lambda \in \Sigma$
	- FALSO  $\{a, b\} \cap \lambda = \varnothing$
- $\lambda \in \Sigma^{*}$
	- VERDADERO pues la [[Alfabeto#Clausura Kleene]] incluye $\lambda$
- $\lambda \in \Sigma^{+}$
	- FALSO porque se puede ver en [[Alfabeto#Clausura Positiva (Excluye la palabra vacía)]]
- $\{\lambda\} = \Sigma^{0}$
	- VERDADERO 
- $\{\lambda, a\} = \Sigma^{1}$
	- FALSO pues falta b
- $\{a, b\} = \Sigma^{1}$
	- VERDADERO
# 3 
Considerando Σ1 = {a, b} y Σ2 = {b, c}, calcular:
- $\Sigma_1 \cup \Sigma_2 = \{a, b, c\}$
- $\Sigma_1 \cdot \Sigma_2 = \{ab, ac, bb, bc\}$
- $\Sigma_1 \cdot \Sigma_2^{+} = \{abcbc, bbbbb, bcccb, ab, \ldots\}$
- $(\Sigma_1 \cdot \Sigma_2)^{*} = \{\lambda, abacbbbcabacbbbc, ab, ac, abbb, \ldots\}$

# 4
Escribir por lo menos 3 cadenas que pertenezcan a cada uno de los siguientes lenguajes:
- $L_1 = \{0^n1^n ~/~ n \gt 0\}$
	- 001
	- 000111
	- 0111111111111111111111111
- $L_2 = \{0^i1^j ~/~ 0 \leq i \leq j\}$
	- 11111
	- 0001111
	- 011
- Sea $\Sigma = \{a, b, c, d\}$ luego $L_3 = \{x~/~ x \in \Sigma^{*}, x ~contiene~la~ subcadena~ ab~ y~ no~ contiene ~la ~subcadena ~bc\}$ 
	- ab
	- abdc
	- dcbaabd
- $L_4 = \{a^nb^md^{m+n} ~/~ n,m \geq 0\}$
	- abdd
	- aabddd
	- aaaaaabbbbbbdddddddddddd

# 5
1. $L_1 = \{0^{2\cdot n}1^{n} ~/~ n \gt 0\}$
2. $L_2 = \{axb^{n}xa ~/~ x \in \Sigma^{*} \land n \geq 3\} = \{x~/~ x \in \Sigma^{+} ~y~x~empieza~en~a~,~termina~en~a~y~tiene~mas~de~3~b's~consecutivas~entre~medio\}$

# 6
Sea L = {ab, aa, baa}, ¿cuáles de las siguientes palabras pertenecen a L+?
- a, b, c

# 7
[[Lenguaje#Operaciones con lenguajes]]
1. $(L_1 \cdot L_1)\cap L_3$
	1. $\{\lambda, a, ab, aa, aab, aba, abab\} \cap \{xb\} = \{ab, aab, abab\}$
2. $\{\{xa\} \cup \{\lambda, a, ab\} / x \in A^{*} \}$ 
2. $L_1^{R} = \{\lambda^{R}, a^{R}, (ab)^{R}\} = \{\lambda, a, ba\}$
	1. $\{\lambda, a, ba\} - \{xa\} = {\lambda}$
3. $\{\lambda, a, ab\}\cdot \{\lambda, a, ba\} = \{\lambda, a, ba, aa, aba, abba\}$
# 8 
Recordar [[Inducción Estructural]]

> Demostrar que el número máximo de nodos que puede haber en un árbol binario de altura n es $2^{n+1}− 1$

Arranco con inducción estructural donde
$P(base)$ : un árbol de altura 0 tiene como máximo $2^{0+1} -1 = 1$ nodos
$P(T)$ : T tiene altura n
##### Demostración
Dos arboles de altura $k = n-1$ se les pone un nodo más arriba
$maxNodos(T) = \overbrace{2^{k+1} -1}^{subarbol~1} + \overbrace{2^{k+1} -1}^{subarbol~2} + \overbrace{1}^{ultimo~nodo} = 2\cdot2^{k+1} - 1 = 2^{k+1+1} -1 = 2^{k+2}-1$

Luego como el arbol ahora es de altura  n-1+1 =n  reemplazando k con n-1 obtenemos $2^{n-1+2}-1 = 2^{n+1}− 1$  verificandose que es el máximo número de nodos


# 9
> Dar una [[Inducción Estructural#Definición rescursiva de estructura]] del **inverso de una cadena**. Demostrar usando inducción estructural que $(\omega_1 \cdot \omega_2)^{r} = \omega_2^{r} \cdot \omega_1^{r}$

- Caso Base : sea la cadena $\lambda \Rightarrow \lambda ^{r} = \lambda$
- Paso Inductivo : sea la cadena $x \in \Sigma^{*}$ y $a$ un caracter arbitrario del alfabeto $\Rightarrow (xa)^{r} = a (x)^{r}$ 

##### Demostración de $(\omega_1 \cdot \omega_2)^{r} = \omega_2^{r} \cdot \omega_1^{r}$ con [[Inducción Estructural#Inducción estructural]]

- $P(base) :$ sea $\omega_1 = \omega_2 = \lambda \Rightarrow (\lambda \cdot \lambda)^{r} = \lambda^{r} \cdot \lambda^{r} = \lambda$ 
- $P(X)$ : sea $\omega_1 = \omega_1' x$ y $\omega_2 = \omega_2' y$ 
	- $|\omega_1| = |\omega_1'| - 1$ donde $\omega_1 = \omega_1' x$
	- Reemplazando en la hipotesis $(\omega_1'x \cdot \omega_2'y)^{r} = (\omega_2'y)^{r} \cdot (\omega_1'x)^{r}$ 
	- $\Rightarrow \underbrace{y(\omega_1'x\cdot\omega_2)^{r}}_{1} = \underbrace{y(\omega_2')^{r} \cdot x(\omega_1)^{r}}_{2}$
	- de 1 : $\Rightarrow y (\omega_2')^{r}\cdot (\omega_1' x)^{r} = y(\omega_2')^{r} \cdot x(\omega_1')^{r}$
	- Vemos que de 1 pudimos obtener 2 para un paso previo y así recursivamente.

# 10
> Demostrar que en una fórmula proposicional bien formada la cantidad de paréntesis izquierdos es igual a la cantidad de paréntesis derechos.

- $PI:$ # Paréntesis izquierdos
- $PD:$ # Paréntesis derechos
- $P(base) :$ Sea la fórmula $F = \varnothing \Rightarrow PI = PD = 0$
- $P(X) :$ 
	- $F_1, F_2 :$ fórmulas de la lógica proposicional bien formadas
	- $\Rightarrow (PI)_{F_1} = (PD)_{F_1} \land (PI)_{F_2} = (PD)_{F_2}$
	- Luego para generar $F_N$ (fórmula nueva) hay un par de opciones
		- $F_N = (F_1 \land F_2)$
		- $F_N = (F_1 \lor F_2)$
		- $F_N = (F_1 \Rightarrow F_2)$
		- $F_N = \lnot F_1$
	- En todos los casos se agrega un por izquierda y otro por derecha manteniendose que $PI - PD) = 0$ 

# 11


# 12

> $S \subset L$

**Demostración por inducción estructural**

- $P(base) :$ $\lambda \in S \Rightarrow  w, |w|_a = |w|_b = 0 \Rightarrow w \in L$ 
- $P(s) :$
	- Si $\underbrace{x \in S}_{x\in L} \Rightarrow \underbrace{axb}_{w \in S} \in S$
		- La tesis implica probar que $\forall s \in S$ la cadena $s$ también se encuentra en $L$ (esto se denota como $T(s)$)
		- $x$ es subestructura de $w$
		- Tengo que demostrar que $w \in L$
		- Si $w = axb \in S$ entonces se obtuvo a partir de la subestrucutra de $x$.
		- Como $x \in S$ por hipotesis, entonces debe ser que $T(x)$ es verdadera ya que evidentemente $x$ es una subestructura de $w$ y por ende $|x|_a = |x|_b = n$. Luego $|w|_a =|x|_a +1 = n+1$ y $|w|_b =|x|_b +1 = n+1$
		- $|w|_a = |w|_b \Rightarrow w \in L$
	- Si $x \in S \Rightarrow bxa \in S$
		- Análogo
	- Si $x, y \in S \Rightarrow xy \in S$
		-  $w = xy$ donde $x, y$ ambas subestructuras con 
		- $|x|_a = |x|_b = i$ 
		- $|y|_a = |y|_b = j$ 
		- $|w|_a = |x|_a + |y|_a = i+j$
		- $|w|_b = |x|_b + |y|_b = i+j$
		- $|w|_a = |w|_b \Rightarrow w \in L$


> $S \supset L$

**Demostración por inducción completa sobre la longitud de la palabra**

- **Caso base** $|w| = 0$ 
	- y por lo tanto $w = \lambda$. En particular también $|w|_a$ y $|w|_b$ son iguales que 0.
- **Hipótesis inductiva** $\forall j: |w| = j \lt n \land w \in L \Rightarrow w \in S$
- **Tésis inductiva** $|w| = n \land w \in L \Rightarrow w \in S$

Si $w \in L$ con $|w| =b$ entonce, puede ocurrir cuatro situaciones.
1. $w = axb$ o $w = bxa$
	1. Esn estos dos casso se cumple que $|x| = n-2$ y $|x|_a = |w|_a - 1 = |x|_b$
	2. Así que $x \in L$ con $|x| \lt n$ y por hipótesis inductiva $x \in S$.
	3. Tomando la definición de $S$,
		1. si $x\in S \Rightarrow w = axb \in S$
		2. si $x\in S \Rightarrow w = bxa \in S$
2. $w = axa$
	1. En este casos se cumple que $|x| = n-2$ pero $|x|_a \ne |x|_b$
	2. Dividimos $x = yz$ tal que $y$ es primer subcadena que cumple que $|y|_a = |y|_b -1$
	3. Para la cadena $ay$ se cumple que $|ay| \lt n$ y $|ay|_a = |ay|_b$
	4. Para la cadena $za$ se cumple que $|za| \lt n$ y $|za|_a = |za|_b$
		1. Por **HI** $ay \in S$ y $za \in S$ y por definición de $S$ tenemos que $w = ayza \in S$
3. $w = bxb$
	1. Análogo a 2.

Luego queda demostrado que $L \subset S$

# Adicional
## 1
> El conjunto $P\subset \{a, b\}^{*}$ se define de la siguiente manera
> - $a \in P$
> - Si $x \in P \Rightarrow bxxa \in P$
> 
> Demostrar por inducción estructural que $\forall w \in P$, vale que $|w|_a = 2^{n}-1$ con $n \geq 1$

Veamos que $P$ es un conjunto de $\{\lambda, a, b, aa, bb, ab, ba, aab, \ldots\}$
Entonces $a$ está en $P$ y también cualquier combinacioón $bxxa$ si es que $x$ ya está en $P$. La hipotesis es entonces que la cantidad de a's que hay en cualquier palabra del conjunto $P$ es $2^{n}- 1$ siento $n$ la longitud de la palabra

- $P(base):$  sea 
	- $n = 1 \rightarrow w = a \Rightarrow |w|_a = 2^{1}-1 = 1$
	- $n = 2 \rightarrow w = baaa \Rightarrow |w|_a = 2^{2}-1 = 3$
	- $n = 3 \rightarrow w = b(baaa)(baaa)a \Rightarrow |w|_a = 2^{3}-1 = 7$
- $P(X)$ 
	- Teniendo algo de la forma $bxxa \in P$ entonces el siguiente paso está dentro de los posibles
		- $b(bxxa)(bxxa)a$
			- $|w|_a = |w_{prev}|_a + |w_{prev}|_a +1 = 2^{n} - 1 +2^{n} - 1+ 1 = 2^{n} + 2^{n} - 1 = 2\cdot2^{n} -1 = 2^{n+1}-1$
		- $b(a)(a)a$
			- caso base

