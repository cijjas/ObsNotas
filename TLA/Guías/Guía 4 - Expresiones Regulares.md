![[Tp04 Lenguajes Regulares Expresiones Regulares.pdf]]

# 1
Recordando [[Lenguaje Regular]]

## a
$$L = \{\lambda\} \Rightarrow ER = \lambda$$

## b
$$L = \{a, b\} \Rightarrow ER = a + b$$

## c
Recordar [[Lenguaje Regular#Propiedades de las ER]]
$$L =\{aa, ab, ba, bb\} \Rightarrow ER = aa+ab+ba+bb = a\cdot(a+b)+b\cdot(a+b)$$
## d
$$L =\{\lambda,aa, ab, ba, bb\} \Rightarrow ER =\lambda+ aa+ab+ba+bb = \lambda + a\cdot(a+b)+b\cdot(a+b)$$

## e 
NO REGULAR

## f
$$
L = \{a^{i}b^{j}: i, j \geq 0\} \Rightarrow ER = a^{*}\cdot b^{*}
$$
## g
NO REGULAR

## h
$$
L = \{(ab)^{i}: i \geq 0\} \Rightarrow ER = (ab)^{*}
$$
## i
$$L = \{x =\omega\omega^{r}: \omega \in \{0, 1\}^{*}, |x| \lt 5\} \Rightarrow ER = \lambda + 00+ 11+ 0000+ 1111 + 0110 + 1001$$
## j
NO REGULAR
## k
$$
L = \{a^{m}b^{n}cd^{p}:m, n, p \geq 0\} \Rightarrow ER = a^{*}b^{*}cd^{*}
$$
## l
$$
L = \{a\beta c^{n}: n \geq 0, \beta \in \{a, b\}^{+}\}\Rightarrow ER= a\cdot (a+b)^{+}c^{*}
$$
## m
$$
L = \{\omega \in \{0, 1\}^{*}: \omega~contiene~dos~unos~seguidos\} \Rightarrow ER = (1+0)^{*}11(1+0)^{*}
$$
## n
$$
L = \{\omega \in \{0, 1\}^{*}: \omega~NO~contiene~dos~unos~seguidos\} \Rightarrow ER = 0^{*}10^{*}\ldots =0^{*}(10^{+})^{*}(0^{*} + 1)
$$
