# Cota de Hamming

1. Enunciar el teorema de la cota de Hamming y probarlo.

---

## Definicion

Dada una palabra $v\in \{0,1\}^n$, y un numero natural $r\geq0$, definimos el ****************************************************disco de radio $r$ alrededor de $v$** como: $D_r=\{w\in \{0,1\}^n: d(v,w)\leq r\}$,es decir, el conjunto de palabras que estan a una distancia menor que $r$ de la palabra $v$.

## Teorema

Sea $C$ un codigo de longitud $n$, $\delta(C)=\delta$ y  $t=\frac{\delta-1}{2}$, entonces:

$$
|C|\leq \frac{2^n}{\sum_{r=0}^{t}{{n}\choose{r}}}
$$

## Prueba

Sea $A=\bigcup_{v\in C}{D_t(v)}$, es decir la union de todos los discos de radio $t$ que se pueden formar al rededor de todas las palabras del codigo $C$.

Como $C$ corrige $t$ errores, vemos que $D_t(x)\cap D_t(y)=\empty$ para todo $x\neq y\in C$, por lo tanto la union que forma $A$ es disjunta, lo cual nos permite decir que $|A|=\sum_{v\in C}{|D_t(v)|}$.

Para calcular la cardinalidad de los $D_t$, vemos que lo podemos ver en capas de $0$ a $t$ de palabras, en la $k$-esima capa, las palabras varian en $k$ digitos del centro (el centro es la palabra que si pertenece al codigo). Por lo tanto tenemos:

$$
|D_t|=\sum_{r=0}^{t}{n \choose r}
$$

Tambien observemos que $A\subseteq \{0,1\}^n$, por lo que $|A|\leq 2^n$.

Juntando todo tenemos:

$$
\begin{align*}
|A|&=\sum_{x\in C}{|D_t(x)|}\\

&=\sum_{x\in C}{\sum_{r=0}^{t}{n\choose r}}\\

&=|C|{\sum_{r=0}^{t}{n\choose r}}\\
\end{align*}
$$

Despejando obtenemos:

$$
|C|= 

\frac{|A|}{\sum_{r=0}^{t}{n\choose r}}
\leq
\frac{2^n}{\sum_{r=0}^{t}{n\choose r}}

$$

# FIN