# Complejidad de Edmonds-Karp

1. Complejidad del algoritmo de Edmonds-Karp
    - Nota: en la prueba se definen unas distancias, y se prueba que esas distancias no disminuyen en pasos sucesivos de EK. Ud. puede usar esto sin necesidad de probarlo

---

## Prueba

Si $*f_0, f_1, f_2, \dots,$*   etc. son los flujos parciales producidos al correr Edmonds-Karp, queremos ver que hay una cantidad finita de ellos, y dar una cota para ese número.

Como la búsqueda y construcción de los caminos aumentante se hace con $BFS$, cada incremento del flujo tiene complejidad $O(m)$. Así que si probamos que solo puede haber $O(nm)$ flujos aumentantes, tendremos una prueba de complejidad para Edmonds-Karp de $O(nm)\cdot O(m)=O(nm^2)$.

En cada construcción de un camino aumentante al menos un lado se vuelve crítico. El problema es que un lado puede volverse crítico **muchas veces**. Se satura, se vacía un poco, vuelve a saturarse, se vacía completamente, etc… Veamos cuántas veces puede pasar esto:

Supongamos que un  $\overrightarrow{xy}$ se vuelve critico en el paso $k$ y luego en el paso $r$. Tenemos que analizar ******dos****** casos:

- Se vuelve critico en el paso $k$ porque se saturo
- Se vuelve critico en el paso $k$ porque se vacío

### CASO A: se saturo en el paso $k$

Como se saturo en el paso $k$, entonces para construir $f_{k+1}$ se debe usar un $f_k$-camino aumentante de la forma $s\dots xy\dots t$. ****************************************************************Como estamos usando Edmonds-Karp**************************************************************** ese camino es de longitud minima, por lo tanto:

$$
\begin{equation}

d_k(y)=d_k(x)+1
\end{equation}
$$

Parar que se vuelva critico de vuelta en el paso $r$, debe pasar una de dos cosas:

- Se vuelve critico en el paso $r$ porque vuelve a saturarse.
- Se vuelve critico en el paso $r$ porque se vacía.

Para que ocurra el primer caso, debe haberse vaciado **antes** aunque sea un poco, si no es imposible que vuelva a saturarse.

Entonces en cualquiera de los dos casos, deducimos que existe un $h$ con $r>h>k$ tal que el flujo en $\overrightarrow{xy}$ disminuye al pasar de $f_h$ a $f_{h+1}$ ya sea vaciándose completamente o un poco.

Esto implica que para construir $f_{h+1}$ se usa un camino $f_h$-camino aumentante de la forma $s\dots\overleftarrow{yx}\dots t$.

**Como estamos usando** **Edmonds-Karp**, ese camino es de longitud minima, por lo tanto:

$$
\begin{equation}
d_h(x)=d_h(y)+1
\end{equation}
$$

Entonces:

$$
\begin{align*}

d_h(t)&=d_h(x)+b_h(x)\\ 
&=d_h(y)+1+b_h(x)&\text{por (2)}\\
&\geq d_k(y)+1+b_k(x)&\text{las distancias no disminuyen}\\
&=d_k(x)+1+1+b_k(x)&\text{por (1)}\\
&=d_k(x)+b_k(x)+2 \\
&=d_k(t)+2
\end{align*}
$$

Concluimos que $d_h(t)\geq d_k(t)+2$

### CASO B: se vacía en el paso $k$

El análisis es similar, como se vacía, existe un camino de la forma $s\dots\overleftarrow{yx}\dots t$ que se usa para pasar de $f_k$ a $f_{k+1}$. **Como estamos usando Edmonds-Karp:**

$$
\begin{equation}
d_k(x)=d_k(y)+1
\end{equation}
$$

Parar que se vuelva critico de vuelta en el paso $r$,debe pasar una de dos cosas:

- Se vuelve critico en el paso $r$ porque vuelve a saturarse
- Se vuelve critico en el paso $r$ porque se vacía

En el primero de estos casos estamos mandando fujo en el paso $r$, pero en el segundo, si estamos diciendo que debe vaciarse, entonces **********antes********** debe haberse llenado aunque sea un poco.

Así que en cualquier caso debe haber un $h$ tal que  $r>h>k$ para el cual se manda flujo a traves de el. Entonces, existe un camino de longitud minima de la forma $s\dots xy\dots t$ que se usa para pasar de $f_h$ a $f_{h+1}$. Por lo tanto:

$$
\begin{equation}
d_h(y)=d_h(x)+1
\end{equation}
$$

**[ 3 ]** y **[ 4 ]** son iguales a **[ 1 ]** y **[ 2 ]**, solo que con $x$ e $y$  intercambiados. Por lo tanto podemos deducir  $d_h(t)\geq d_k(t)+2$ de la misma forma que lo que hicimos con el caso en que sea saturaba en el paso $k$, simplemente intercambiando $x$ e $y$  en la prueba.

Así que también en este caso concluimos que  $d_h(t)\geq d_k(t)+2$

## Volviendo a la prueba…

Concluimos que en cualquiera de los casos, luego de que un lado se vuelve crítico, para que pueda volverse crítico otra vez, la distancia entre $s$ y $t$  debe aumentar en al menos $2$. 

Como la distancia entre $s$ y $t$  puede ir desde un mínimo de $1$  a un máximo de $n − 1$, concluimos que un lado puede volverse critico un máximo de  $O(\frac n2)=O(n)$ veces.

Como cada camino aumentante que se usa en Edmonds-Karp tiene al menos un lado que se vuelve critico, entonces el total de flujos intermedios está acotado por $O(nm)$, pues hay $m$ lados y cada uno se puede volver critico a lo sumo $O(n)$ veces.

Como cada construcción de un flujo tiene complejidad $O(m)$ concluimos que la complejidad de Edmonds-Karp es de $O(m)\cdot O(nm)=O(nm^2)$

# FIN