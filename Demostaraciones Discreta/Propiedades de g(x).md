# Propiedades de g(x)

1. Sea $C$ un codigo ciclico de dimension $k$ y longitud $n$ y sea $g(x)$ su polinomio generador. Probar que:
    1. $C$ esta formado por los multiplos de $g(x)$ de grado menor que $n$: 
        
        $$
        C = \{ p(x) : gr(p) < n \land g(x) \mid p(x)\}
        $$
        
    2. $C=\{v(x) \odot g(x): v(x) \text{ es un polinomio cualquiera}\}$
    3.  $gr(g(x)) = n − k$
    4. $g(x) \mid (1+x^n)$

---

## Prueba 1. y 2.

Sea:

- $C$ un codigo ciclico de longitud $n$
- $C_1 = \{ p(x) : gr(p) < n \land g(x) \mid p(x)\}$
- $C_2=\{v(x) \odot g(x): v(x) \text{es un polinomio cualquiera}\}$

Pobaremos que $C \subseteq C_1 \subseteq C_2 \subseteq C$:

### $C\subseteq C_1$:

Sea $p(x)\in C$.

Dividamos a $p(x)$ por $g(x)$ obteniendo asi $q(x)$ y $r(x)$ con $gr(r)<gr(g)$ tal que $p(x)=q(x)\cdot g(x)+r(x)$.  Por lo tanto $r(x)=p(x)+q(x)\cdot g(x)$. 

Como $gr(r)<gr(g)<n$, entonces $r(x)=r(x)\,\ mod \,\ (1+x^n)$.

Como $p(x)\in C$, entonces $gr(p)<n$ y $p(x)=p(x)\,\ mod \,\ (1+x^n)$, entonces:

$$
\begin{align*}

r(x)&=r(x)\,\ mod \,\ (1+x^n)\\

&= (p(x)+q(x)\cdot g(x))\,\ mod \,\ (1+x^n)\\

&=p(x) \,\ mod \,\ (1+x^n) + (q(x)\cdot g(x))\,\ mod \,\ (1+x^n)\\

&= p(x)+ q\odot g

\end{align*}
$$

Como $p(x)\in C$ y $q\odot g\in C$ y $C$ es lineal, conlcuimos que $r\in C$. Pero $gr(r)<gr(g)$ que es el polinomio no nulo con el menor grado en $C$. Concluimos que $r=0$. 

Por lo tanto  $p(x)=q(x)\cdot g(x)+r(x) \in C$.

### $C_2 \in C$:

Probaremos que si $w\in C$ y $p$ es una palabra cualquiera, entonces $p\odot w\in C$.

Sabemos que la rotacion de una palabra perteneciente al codigo pertenece al codigo. Entonces:

$$
\begin{align*}

p\odot w &= \Big ( \sum_{i=0}^{n}{p_i x^i}\Big) \odot w \\

&= \sum_{i=0}^{n}{p_i(x^i \odot w)} \\

&= \sum_{i=0}^{n}{p_i(rot_i(w))} \\

 
\end{align*}
$$

Como el codigo es lineal, las combinaciones lineales de cualquier palabra en el codigo estan en el codigo. Concluimos que $p\odot w\in C$.

Para probar lo que nosotros queremos, tomamos $w=g(x)$.

### $C_1\in C_2$:

Esto es obvio, pues si $gr(p)<n$ y $p(x)=q(x)g(x)$, entonces $p(x)=p(x)\,\ mod\,\ (1+x^n)$ pues $gr(p)<n$. Por lo tanto $p(x)=q(x)g(x)\,\ mod\,\ (1+x^n)=q\odot g \in C_2$.

## Prueba 3.

Queremos probar que  $gr(g(x)) = n − k$. 

Sea $t$ el grado de $g(x)$.

Por 1, $p(x)\in C$ si y solo si es de la forma $q(x)g(x)$ para algun polinomio $q(x)$.

Pero como el grado de los elementos de $C$ es menor que $n$, entonces el grado de $q(x)g(x)$ debe ser menor que $n$, por lo tanto, el grado de $q(x)$ debe ser menor que $n-t$. Podemos observar que para cada polinomio de grado menor que $n-t$ corresponde un polinomio de $C$ y viceversa.

Por lo tanto, la cardinalidad de $C$ es igual a la cardinalidad del conjunto de polinomios de grado menor que $n-t$. Cada uno de los coeficientes de estos polinomios, pueden ser $1$ o $0$, asi que cada uno tiene 2 posibilidades. Como son $n-t$ polinomios, el total de polinomios posibles es $2^{n-t}$.

Hemos probado que $|C|=2^{n-t}$, pero como $C$ es lineal vale tambien que $|C|=2^k$. 

Por lo tanto:

$$
2^k=2^{n-t} \Longrightarrow k=n-t
$$

Se sigue que $gr(g)=t=n-k$.

## Prueba 4.

Queremos probar que $g(x) \mid (1+x^n)$.

Dividimos entonces $(1+x^n)$ por $g(x)$ obteniendo asi $q(x)$ y $r(x)$ tal que $(1+x^n)=q(x)\cdot g(x)+r(x)$ con $gr(r)<gr(g)$, es decir que $r(x)=q(x)\cdot g(x)+(1+x^n)$, entonces:

$$
\begin{align*}
r(x)&=q(x)\cdot g(x)+(1+x^n)\\

r(x)\,\ mod\,\ (1+x^n)&=(q(x)\cdot g(x)+(1+x^n)) \,\ mod\,\ (1+x^n)\\
&=q(x)\odot g(x)

\end{align*}
$$

Aclaramos que en la ultima igualdad utilizamos $(1+x^n) \,\ mod\,\ (1+x^n) = 0$.

Pero $gr(r)<n\Rightarrow r(x) \,\ mod \,\ (1+x^n)=r(x)$ y por lo tanto $r(x)=q(x)\odot g(x)$. Pero ya probamos que $q(x)\odot g(x)\in C$ y como $gr(r)<gr(g)$ concluimos que $gr(r)=0$, es decir,  $r(x)=0$.

# FIN