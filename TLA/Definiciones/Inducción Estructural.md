# Definición rescursiva de estructura
- Las definiciones recursivas tienen:
	- **Caso Base** en el que se definen una o más estructuras elementales
	- **Paso de inducción** en el que se definen estructuras más complejas en términos de estructuras previamente definidas

# Inducción estructural
  
> Cuando tenemos una definición recursiva, se pueden probar teoremas acerca de ella utilizando inducción estructural.


Sea P(X) una proposición acerca de estructuras X definidas mediante alguna definición recursiva determinada.

P(estructura) es V si 
- P(base) es V
- P(construcciones) es V asumiento P(anterior) es V


> La forma de saber que se puede usar es si la proposicion y la definicipon recursiva son visualizables.

#### Ejemplo

> $P(X)$ : Si $T$ tiene $n$ nodos $\Rightarrow$ tiene $n-1$ arcos

- $P(base)$ : $T$ tiene 1 nodo $\Rightarrow$ tiene 0 arcos
- $P(T)$ : $T$ se construyó a partir de $T_1, \ldots, T_k$ y $P(T_1)$ es verdadera y ... y $P(T_k)$ es verdadera
**Demostración**
1. $nodos(T) = nodos(T_1) + nodos(T_2) + ... +  nodos(T_k) + 1$
2. $aristas~de~T = aristas(T_1) + ... + aristas(T_k) + k = nodos(T_1) - 1 + nodos(T_2) - 1 + ... + nodos(T_k) - 1 + k  = nodos(T_1) + ... + nodos(T_k) - k + k$
$de~1 \Rightarrow aristas~de~T = nodos(T) -1$
