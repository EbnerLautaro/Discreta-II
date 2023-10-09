# Complejidad Hungaro

1. Probar la complejidad $O(n^4)$ del algoritmo Hungaro y dar una idea de como se la puede reducir a $O(n³)$.

---

## Observacion

Luego de un cambio de matriz, o bien se extiende el matching, o bien $|S|$ aumenta.

**Prueba:**

Luego de un cambio de matriz, tenemos (al menos) un nuevo cero en $S\times \overline{\Gamma(S)}$, es decir, en alguna fila $i$ de $S$ interseccion alguna columna $j$ de $\overline{\Gamma(S)}$. Pero entonces la columna $j$ se etiqueta con $i$ y se revisará. Tenemos dos casos posibles:

1. La columna $j$ esta libre y extendemos el matching.
2. La columna $j$ forma parte del matching, es decir, existe una fila $k$ matcheada con la columna $j$. Entonces la fila $k$ se etiquete con $j$ y tenemos un nuevo $S$ con cardinalidad mayor.

Entonces terminamos con una extension del matching ó  se produce un nuevo $S$ con cardinalidad mayor. ****

## Teorema

La complejidad del algoritmo Hungaro ******************************************como lo implementamos****************************************** es $O(n^4)$.

## Prueba

El algoritmo consta de realizar un matching inicial y extenderlo la cantidad de veces necesarias hasta llegar un matching perfecto.

Vamos probando por separado:

1. $O(\text{"Matching inicial"})$:
    
    Para hacer el matching inicial, hay que revisar $n$ filas y por cada una de ellas, $n$ columnas, entonces es $O(n^2)$.
    
2. $O(\text{"Cambio de matriz"})$:
    
    Para hacer un cambio de matriz, necesitamos hacer lo siguiente:
    
    - Buscar el minimo elemento $m$ en $S\times \overline{\Gamma (S)}$, lo cual es $O(n^2)$.
    - Sumar $m$ a $\overline S\times \Gamma(S)$, lo cual es $O(n^2)$.
    - Restar $m$ a $S\times \overline {\Gamma(S)}$, lo cual es $O(n^2)$.
    
    Concluimos que la complejidad del cambio de matriz es $O(n^2)$.
    
3. $\text{Cantidad de cambios de matriz}$:
    
    Como $|S|$ solo puede crecer $n$ veces, tenemos que hay a lo sumo $n$ cambios de matriz antes de extender el matching.
    
4. $O(\text{"Extender el matching"}):$
    
    Extender el matching consta de cambiar la matriz las veces necesarias (buscando $m$ en cada una) para poder extender el matching. Entonces:
    
    $$
    \begin{align*}
    
    O(\text{"Extender matching"})
    &=\\
    
    (\text{cant cambio matriz}) \cdot O(\text{Cambio de matriz}) &=\\
    
    n\cdot O(n^2)&=\\
    O(n^3)
    
    \end{align*}
    $$
    

Para terminar, aclaramos como maximo, pordemos extender el matching $n$ veces, entonces **la complejidad total** **del algortimo Hungaro** es:

$$
\begin{align*}

O(\text{"matching inicial"})+O(\text{"Extencion"})\cdot (\text{cant extenciones}) &=\\

O(n^2)+O(n^3)\cdot n &=\\
O(n^4)

\end{align*}
$$

Queda probado que la complejidad del algortitmo Hungaro es $O(n^4)$.

## Idea para complejidad $O(n^3)$

Para lograr una mayor eficiencia y llevar el algoritmo a $O(n^3)$ nos concentramos en bajar la complejidad de la extension. En lugar de recorrer la matriz sumando o restando $m$ (esto es $O(n^2)$) se construye un registro auxiliar donde se indica para cada entrada de la matriz cuanto hay que sumarle o restarle cada vez que se lo lea, lo que seria $O(n)$ en vez de $O(n^2)$.

# FIN