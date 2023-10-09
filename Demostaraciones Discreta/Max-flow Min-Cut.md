# Max-flow Min-Cut

1. Probar que el valor de todo flujo es menor o igual que la capacidad de todo corte y que si  $f$ es un flujo, entonces las siguientes afirmaciones son equivalentes:
    1. Existe un corte $S$  tal que $v(f) = cap(S)$. (y en este caso, $S$ es minimal)
    2. $f$ es maximal.
    3. No existen $f$-caminos aumentantes.

---

## Estructura

Hay que probar dos cosas:

1. Probar que el valor de todo flujo es menor o igual que la capacidad de todo corte 
2. Si  $f$ es un flujo, entonces las siguientes afirmaciones son equivalentes:
    1. Existe un corte $S$  tal que $v(f) = cap(S)$. (y en este caso, $S$ es minimal)
    2. $f$ es maximal.
    3. No existen $f$-caminos aumentantes.

## Prueba 1:

Sea $f$ flujo y $S$ corte, entonces: 

$$
\begin{align*}

v(f)&=f(S,\bar S)-f(\bar S,S) \\
&\leq f(S,\bar S) \\
&\leq c(S,\overline S)= CAP(S)

\end{align*}
$$

## Prueba 2:

Vamos a probar que $a\Rightarrow b \Rightarrow c \Rightarrow a$:

### Prueba $a \Rightarrow b$:

Probaremos que si existe un corte $S$  tal que $v(f) = CAP(S)$  entonces $f$  es maximal y $S$ es minimal.

Sean $S$  y $f$ como el enunciado y sea $g$ un flujo cualquiera.

Sabemos que $v( g)\leq CAP(S)$, pero por hipotesis tenemos que $v(f) = cap(S)$  entonces $v( g)\leq CAP(S) = v(f)$. Concluimos que $f$ es flujo maximal. 

Ademas, si $T$ es un corte, $CAP(T)\geq v(f)=CAP(S)$ lo que implica que $S$ es corte minimal.

### Prueba $b \Rightarrow c$:

Probaremos que si $f$ es maximal entonces no existen $f$-caminos aumentantes.

Si existiese un $f$-camino aumentante, podriamos mandar $\epsilon > 0$  a travez de el, por lo que obtendriamos un flujo $f^*$ tal que $v(f^*)=v(f)+\epsilon$. Esto diria que $v(f^*)>v(f)$ lo cual contradice que $f$ sea maximal.

### Prueba $c\Rightarrow a$:

Probaremos que si no existen $f$-caminos aumentantes entonces existe un corte $S$ tal que $v(f)=CAP(S)$.

Suponemos el antecedente y probamos:

Sea $S=\{s\}\cup \{x \in V: \exist f$-camino aumentante desde $s$ a $x\}$. Como estamos suponiendo que no existen $f$-caminos aumentantes, $t\not \in S$, por lo que $S$ es corte, entonces $v(f)=f(S,\bar S) - f(\bar S, S)$, analicemos cada termino:

- $f(S,\bar S)$:
    
    $$
    f(S,\bar S)= \sum\limits_{\substack{x\,\in\,S \\ y \,\not \in\,S\\ \overrightarrow{xy}\in E }} f(\overrightarrow{xy} )
    $$
    
    Como $x\in S$ entonces, existe un camino aumentante entre $s$ y $x$ y como $y\not \in S$, podemos ver que no existe un camino aumentante entre $s$ y $y$. En particular $s\dots xy$ **NO** es un camino aumentante. La unica razon por la cual no es un $f$-camino aumentante es porque no podemos usar el lado $\overrightarrow{xy}$ por estar saturado, es decir $f(\overrightarrow{xy})=c(\overrightarrow{xy})$. Esto es cierto para todo $\overrightarrow{xy}$ que aparezca en la suma. Entonces:
    
    $$
    \begin{align*}
    
    f(S,\overline S) &= \sum\limits_{\substack{x\,\in\,S \\ y \,\not \in\,S\\ \overrightarrow{xy}\in E }} f(\overrightarrow{xy})\\
    &= \sum\limits_{\substack{x\,\in\,S \\ y \,\not \in\,S\\ \overrightarrow{xy}\in E }} c(\overrightarrow{xy})\\
    &= c(S,\overline S)=CAP(S)
    \end{align*}
    $$
    
- $f(\bar S,S)$:
    
    $$
    \begin{align*}
    f(S,\overline S) &= \sum\limits_{\substack{x\not\in S \\ y \in S\\ \overrightarrow{xy}\in E }} f(\overrightarrow{xy})
    \end{align*}
    $$
    
    Como $y\in S$ entonces, existe un camino aumentante entre $s$ y $y$ y como $x\not \in S$, podemos ver que no existe un camino aumentante entre $s$ y $x$. En particular $s\dots yx$ **NO** es un camino aumentante. La unica razon por la cual no es un $f$-camino aumentante es porque no podemos usar el lado $\overrightarrow{xy}$ backward, es decir, que $f(\overrightarrow{xy})=0$. Esto es cierto para todos los terminos de esa sumatoria
    

$$
\begin{align*}

f(S,\overline S) &= \sum\limits_{\substack{x\not\in S \\ y \in S\\ \overrightarrow{xy}\in E }} f(\overrightarrow{xy})\\

&=  \sum\limits_{\substack{x\not\in S \\ y \in S\\ \overrightarrow{xy}\in E }} 0\\
&=0

\end{align*}
$$

Retomando, tenemos que 

$$

\begin{align*}
v(f)&=f(S,\bar S) - f(\bar S, S)\\
&=CAP(S)-0\\
&=CAP(S)
\end{align*}
$$

# FIN