Un alfabeto $\Sigma$ es un conjunto finito no vacío de símbolos. 
#### Ejemplos
1. $\Sigma = \{0, 1\}$
2. $\Sigma = \{a,b,c,\ldots , z\}$

# Cadena
Una cadena o palabra es una secuencia finita de símbolos seleccionados de algún alfabeto.
#### Ejemplo
00001010 es una palabra dentro del alfabeto binario

# Longitud de una cadena
La longitud de una cadena es la cantidad de posiciones que ocupan los símbolos que tiene.
## Longitud recursiva
Base : $|\lambda| = 0$
Construcción: $|\omega x| = |\omega| + 1$
#### Ejemplo
00001010 es una palabra de longitud 8.


# La cadena vacía
La cadena vacía $\lambda$ (a veces $\epsilon$) es una cadena de longitud 0.
#### Ejemplo
$\lambda = a^0$

# Potencias de un alfabeto

> Es el conjunto de cadenas de una determinada longitud sobre el alfabeto.

Si $\Sigma$ es un alfabeto, podemos expresar el conjunto de todas las cadenas de una determinada longitud de dicho alfabeto utilizando una notación exponencial.
Es decir:

$\Sigma ^{k} = \{\omega~con~simbolos~en~ \Sigma / |\omega| = k\}$

#### Ejemplos
Si $\Sigma = \{0, 1\}$
entonces
$\Sigma^{0} = {\lambda}$
$\Sigma^{1} = \{0, 1\}$
$\Sigma^{2} = \{00, 01, 10, 11\}$
# Clausuras de un alfabeto

## Clausura Kleene
A la unión generalizada de todas las potencias de un alfabeto se la denomina clausura Kleene $\Sigma ^{*}$ donde:
$\Sigma ^{*} = \overbrace{\Sigma^{0}}^{\lambda} \cup \Sigma^{1} \cup \ldots \cup \Sigma^{n}$

## Clausura Positiva: (Excluye la palabra vacía)
Si se excluye la cadena vacía se denomina clausura positiva $\Sigma ^{+}$
$\Sigma ^{+} = \Sigma^{1} \cup \Sigma^{2} \cup \ldots \cup \Sigma^{n}$

Luego, $\Sigma^{+} = \Sigma^{*}- \{\lambda\}$

# Concatenación de cadenas
Si x es la cadena compuesta por i símbolos: $x = x_0x_1 \ldots x_{i-1}x_i$
E y es la cadena de j símboolos : $y = y_0y_1 \ldots y_{j-1}y_j$
Entonces xy es la cadena de i+j símbolos 
$xy = x_0x_1 \ldots x_{i-1}x_iy_0y_1 \ldots y_{j-1}y_j$

## Propiedades de la concatenación
- Cerrada: la concatenación de cadenas es una cadena.
	- La concatenación de palabras es otra palabra sobre el mismo alfabeto
	- $\forall x, y \in \Sigma^{*}:x\cdot y \in \Sigma^{*}$
- Asociatividad: 
	-  $\forall x, y, z \in \Sigma^{*}:x\cdot (y\cdot z) = (x\cdot y ) \cdot z$
- Elemento neutro: la palabra vacía λ
	- $\forall x \in \Sigma^{*}:\lambda \cdot x = x \cdot \lambda = x$

# Reverso de una palabra
Si $\omega = a_1a_2\ldots a_n$ es una palabra sobre $\Sigma$ entonces la palabra inversa, o refleja de $\omega$ se define como $\omega^{r} = a_n\ldots a_1$

## Reverso recursivo
Base: $\lambda ^{r} = \lambda$
Construcción $(\omega x)^{r} = x (\omega)^{r}$
Luego se aplica lo mismo todo el tiempo a $\omega$ y termina obteniendose el reverso
