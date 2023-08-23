> Dado un alfabeto $\Sigma$, los símbolos $\varnothing$ , $\lambda$ y los operadores $+$ (unión), $.$ (concatenación), ) y $*$ (clausura) y los paréntesis $($ y$)$, definimos una **EXPRESIÓN REGULAR (ER)** sobre el alfabeto $\Sigma$ como
> Base:
> - El símbolo es una ER.
> - El símbolo es una ER.
> - Cualquier símboloa es una ER
> Paso inductivo:
> - Si $\alpha$ y $\beta$ son ER, entonces $\alpha + \beta$ es una ER.
> - Si $\alpha$ y $\beta$ son ER, entonces $\alpha \cdot \beta$ es una ER.
> - Si $\alpha$ es una ER, entonces $\alpha^{*}$ es una ER.
> - Si $\alpha$ es una ER, entonces $(\alpha)$ es una ER.

# Lenguaje descripto por ER
![[Pasted image 20230823151811.png]]

# Precedencia de operadores
1. *
2. .
3. +



# Propiedades de las ER

## Equivalencia de ER's
> Dos ER's $r_1, r_2$ son equivalentes si describen el mismo lenguaje, es decir $L(r_1) = L(r_2)$

## Propiedades 
![[Pasted image 20230823152322.png]]



# Conversión de [[Autómatas Finitos]] a ER

## Teorema de análisis de Kleene

>Todo lenguaje definido mediante un AFD también ese define mediante una $ER$

> Si $L$ es un lenguaje aceptador por un autómata finito $M$, entonces existe una expresión regular $\alpha$ tal que $L = L(M)=L(\alpha)$

### Método de Ecuaciones Características

1. Obtener las ecuaciones características del autómata.
2. Resolver el sistema de ecuaciones.
3. Obtener la solución para el estado inicial.

Sea $x_i = \alpha_{i0}+\alpha_{i1}x_1 + \ldots + \alpha_{in}x_n$. Donde cada $a_{ij}$ es una ER. una solución para $x_i$ es una ER.
A una ecuación de la forma $X = \alpha X + \beta$ donde $\alpha, \beta$ son ER, se llama **ecuación fundamental** de ER's.

> **Lema de Arden**
> $$
X = \alpha X + \beta \iff X= a^{*}\beta ~y~es~unica~si~ \lambda \notin L(\alpha)
$$
![[Pasted image 20230823154439.png]]

#### Ejemplo
```mermaid
stateDiagram
direction LR
[*] --> q1
q1 --> q2 : b
q2 --> q1: a, b
q1 --> q1 : a
q2 --> [*]
```
$$q_1 = aq_1 + bq_2 \tag{1}$$
$$q_2 =\lambda + aq_1 + bq_1 \tag{2}$$

Luego por distributiva
$$q_2 = \lambda + (a+b)q_1 \tag{3}$$

Por lema de Arden
$$q_1 = a^{*}bq_2 \tag{4}$$

Por (4) y (3)

$$
q_2 = \lambda + (a+b)a^{*}bq_2 \tag{4.5}
$$
Nuevamente por Arden
$$
q_2 = \lambda + ((a+b)a^{*}b)^{*}\lambda = ((a+b)a^{*}b)^{*} \tag{5}
$$
Luego en (4) con (5) 
$$
q_1 =a^{*}b((a+b)a^{*}b)^{*}
$$





# Conversión de ER a [[AFD - Autómatas Finitos Deterministicos]]

## Teorema de Síntesis de Kleene
> Todo lenguaje definido por una ER puede definirse mediante un AFND-$\lambda$

Obvio que entonces vale también que  $ER \Rightarrow AFND-\lambda$


## Método de composición de autómatas
> Este autómata tiene un único estado de aceptación y ningún arco que entre al estado inicial o que salga del estado de aceptación.


