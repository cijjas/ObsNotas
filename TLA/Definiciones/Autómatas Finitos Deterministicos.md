## Función de transición (AFD)
> En los AFD la función de transición se define $\delta : Q \times \Sigma \rightarrow Q$

A cada par (estado, símbolo) le corresponde uno y sólo un estado.

## Función de transición extendida
> La función de transición extendida $\hat{\delta}$ describe lo que ocurre cuando se parte de cualquier estado y se sigue una secuencia de entradas. Se construye por inducción a partir de $\delta$ .
> - $\hat{\delta}: Q \times \Sigma^{*} \rightarrow Q$

**Demo por induccion**
Base: $\hat{\delta} (q, \lambda) = q$
Paso inductivo: con $w = w'a$ se obtiene $\hat{\delta} (q, w'a) = \delta (\hat{\delta}(q, w'), a)$

## Configuración instantánea
> La configuración instantánea es una descripción del autómata finito en un momento dado.
> Se denota con un par $[q, \omega]$, donde q es un estado y $\omega \in \Sigma ^{*}$
### Secuencia de configuraciones
> El simbolo $\mapsto$ indica el movimiento válido entre dos configuraciones.
> Es decir $[q, aw] \mapsto [p, w] \iff \delta(q, a) = p$
#### Ejemplo 
$[q_0, 01]\mapsto [q_1, 1] \mapsto [q_3, \lambda]$

## Lenguaje aceptado por un Autómata Finito Determinista
- El lenguaje de un AFD es $L = \{\omega \in \Sigma ^{*} / \hat{\delta}(q_0, \omega) \in F\}$
- El lenguaje de un AFD es $L = \{\omega \in \Sigma^{*} /~ [q_0, \omega] \mapsto ^{*}[p, \lambda], p \in F\}$
## Equivalencia de autómatas
> Dos AFD $M$ y $M’$ son equivalentes si y sólo si $L(M)=L(M’)$
> Es decir, dos autómatas $M$ y $M’$ son equivalentes si y sólo si reconocen el mismo lenguaje.
- Si una palabra es reconocida en uno y en otro no, no son equivalentes
- La minimización de dos autómatas equivalentes es única.
## AFD Mínimo
> AFD Mínimo $\rightarrow$ AFD equivalente con la menor cantidad de estados.

### Minimización de un AFD
#### Estados accesibles
> Si existe manera de llegar desde $q_0$.
> - Un estado $q_i \in Q$ es **accesible** si $\exists \alpha \in \Sigma^{*}/ \hat{\delta}(q_0, \alpha) = q_i \in Q$
> - Un estado $q_i \in Q$ es **accesible** si $\exists \alpha \in \Sigma^{*}/ [q_0, \alpha] \mapsto ^{*} [q_i, \lambda]$

#### Estados equivalentes o indistinguibles
> Los estados p y q son indistinguibles si para toda cadena de entrada $\omega$, $\hat{\delta}(p, \omega)$ es un estado de aceptación (estado final) si y sólo si $\hat{\delta}(q, \omega)$ es un estado de aceptación.
> Simbólicamente, **p indistinguible de q si**
> $\forall \omega \in \Sigma^{*} : \hat{\delta}(p, \omega) \in F \iff \hat{\delta}(q, \omega) \in F$

- Los estados p y q son distinguibles si existe por lo menos una cadena $\omega$ tal que $\hat{\delta}(p, \omega)$ es un estado final y $\hat{\delta}(q, \omega)$ no lo es, o viceversa.
#### Indistinguibilidad de orden k
> La indistinguibilidad de orden k $E_k$ es una relación de equivalencia. Determina una partición del conjunto Q en clases de equivalencia.
![[Pasted image 20230809172822.png]]
![[Pasted image 20230809172842.png]]
