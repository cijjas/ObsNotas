>Una gramática es un sistema matemático para definir un lenguaje. Define la estructura de las palabras de un lenguaje.

Es una 4-tupla $G = (N, \Sigma, P, S)$ donde:
- $N$ es un conjunto finito de símbolos no terminales (variables o categorías sintácticas
- $\Sigma$  es un conjunto finito de símbolos **terminales** $N \cap \Sigma = \varnothing$
- Un elemento $(\alpha, \beta)$ en $P$ se escribe $\alpha \rightarrow \beta$ y se llama **producción** ($\alpha \in (N \cup \Sigma)^{+}$ y $\beta \in (N \cup \Sigma)^{*}$
	- Las producciones son un tipo de transformación
- $S$ es un símbolo distinguido $N$, llamado sentencia o **símbolo inicial**

Básicamente un conjunto de reglas dentro de un lenguaje

# Formas sentenciales
> **Base**: $S$ es una forma sentencial
> **Paso inductivo**: Si $\alpha \beta \gamma$ es una forma sentencial y $\beta \rightarrow \delta \in P$, entonces $\alpha \delta \gamma$ también es una forma sentencial.

Una forma sentencial de G que sólo contiene símbolos terminales o es la palabra vacía se llama sentencia generada por G.


# Lenguaje generado por una gramática
> Un lenguaje generado por una gramática $G$, es decir $L(G)$ es el conjunto de **sentencias** generadas por $G$.

$$L(G) = \{\omega \in \Sigma ^{*} / S \Rightarrow^{*} \omega\}$$



#### Ejemplo
$G = <V, \Sigma, S, P>$
$V = \{S, A\}$
$\Sigma =\{a ,b\}$
$P = \{S \rightarrow aAb, A \rightarrow aAb |a\}$
$\underbrace{S \Rightarrow aAb}_{S \rightarrow aAb \in p} \Rightarrow aaAbb \Rightarrow aaabb$
- Obtengo una cadena terminal y $L(G) = L = \{a^{n+1}b^{n}/~n\geq 1\}$
## Equivalencia de gramáticas
$$\forall \omega : \omega \in L(G_1) \iff \omega \in L(G_2)$$
Para el caso del ejemplo de arriba [[Gramática#Lenguaje generado por una gramática#Ejemplo]]:
$\forall \omega: \omega \in L(G)~ \iff ~\omega \in \{a^{n+1}b^{n}/~n\geq 1\}$


# Clasificación de gramáticas (Jerarquía de Chomsky)

## Gramáticas tipo 0 : Irrestrictas
> Este tipo de gramática puede generar lenguajes formales que son capaces de describir estructuras lingüísticas muy complejas. No hay restricciones en las reglas de producción, excepto que la longitud de la parte izquierda de la regla no puede ser mayor que la de la parte derecha. Las reglas pueden reescribir cualquier combinación de símbolos en cualquier contexto. Los lenguajes generados por este tipo de gramática son los más poderosos en términos de describir lenguajes formales.


Son las más generales. (Gramáticas sin restricciones). Las producciones pueden ser de cualquier tipo permitido, es decir de la forma
> Producciones $\alpha \rightarrow \beta$ donde $\alpha \in (N \cup \Sigma)^{+}$ y $\beta \in (N \cup \Sigma)^{*}$
## Gramáticas tipo 1 : Sensibles al contexto
> Estas gramáticas tienen reglas de producción que deben respetar una restricción de contexto, lo que significa que las sustituciones solo pueden ocurrir si el contexto circundante es apropiado. Pueden generar lenguajes formales más limitados que los de las gramáticas de tipo 0.

> Producciones $\alpha \rightarrow \beta$ donde $|\alpha| \leq |\beta|$ excepto para $S \rightarrow \lambda$

> $\alpha \beta \gamma \rightarrow \alpha \pi \gamma$
## Gramáticas tipo 2 : Libres de contexto
>En este nivel, las reglas de producción son más simples y menos flexibles que en los tipos anteriores. Las gramáticas independientes del contexto son ampliamente utilizadas en la descripción formal de la sintaxis de muchos lenguajes de programación y en la descripción de la estructura de lenguajes naturales.

> Producciones $A \rightarrow \beta$ donde $A \in N = no~terminales$ y $\beta$ es una cualquier cosa.
## Gramáticas tipo 3 : Regulares
> Este tipo de gramática es el más restrictivo y solo puede generar lenguajes regulares. Las reglas de producción son las más simples, y las gramáticas regulares son especialmente adecuadas para describir patrones simples y repetitivos, como los que se encuentran en expresiones regulares y lenguajes formales como los automatas finitos.

|Lineales por izquierda | Lineales por derecha|
|---|-|
|$A \rightarrow Cb$ | $A\rightarrow bC$|
|$A \rightarrow b$ | $A\rightarrow b$|
|$A \rightarrow \lambda$ | $A\rightarrow \lambda$|

# Lenguaje a Autómata
![[Pasted image 20230809155711.png]]

Cada una de estas categorías es correspondiente a un tipo de Autómata que se ve en la Figura 1. de las relaciones Lenguaje - Máquina. En este caso analizamos en profundidad [[Gramática#Gramáticas tipo 3 Regulares]] correspondientes a 
[[Autómatas Finitos]].

