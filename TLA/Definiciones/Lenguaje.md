
# Lenguaje sobre un alfabeto
Un lenguaje sobre $\Sigma$ es cualquier subconjunto de $\Sigma ^{*}$ es decir: $L \subseteq \Sigma^{*}$

#### Ejemplo
$L = \{\omega \in \Sigma ^{*} / \#_a(\omega) = \#_a(\omega)\} = \{abc, acccb, aabb, acbcacbc, \ldots\}$
 
#### Definición recursiva de $L^{i}$
Base : $i = 0$ luego $L^{0} = {\lambda}$
Construcción: $i = n+1$ luego $L^{n+1} = L^{n}L$

## Operaciones con lenguajes
Como con cualquier conjunto se pueden hacer las operaciones
- Unión de lenguajes
- Intersección de lenguajes
- Diferencia de lenguajes
Además, existen las siguientes
- **Producto de lenguajes de concatenación**
	- $L_1 \cdot L_2 = \{\omega / \omega = xy, x \in L_1 \land y \in L_2\}$
- **Potencia de Lenguajes**
	- Consiste en el lenguaje resultante de concatenar el lenguaje consigo i veces.
	- $\underbrace{L^{i} = L \cdot L \cdot \ldots \cdot L}_{i~veces}$
- **Clausura de un Lenguaje**
	- $L^{+} = \bigcup_{i = 1}^{\infty} L^{i}$
- **Clausura de Kleene de un lenguaje**
	- $L^{*} = \bigcup_{i = 0}^{\infty} L^{i}$
- **Reversa de un lenguaje**
	- $L^{r} = \{\omega^{r} / \omega \in L\}$
