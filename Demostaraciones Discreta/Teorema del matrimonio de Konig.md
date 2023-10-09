# Teorema del matrimonio de Konig

1. Enunciar y probar el teorema del matrimonio de Konig.

---

## Teorema

Todo grafo bipartito regular tiene un matching perfecto.

## Estructura

1. Probar que en todo grafo bipartito regular todo matching completo es perfecto.
2. Probar que en todo grafo bipartito regular se cumple la condicion de Hall.

## Prueba

Sea:

- $G=(X\cup Y,E)$.
- Para $W\subseteq V$ definimos $E_W=\{xy\in E:x\in W \lor y\in W\}$.

Supongamos ahora que $W\subseteq X$ ó $W \subseteq Y$:

Como $\chi(G)=2$ sabemos que hay lados, y como $G$ es regular sabemos que existe $\delta =\Delta >0$ tal que $d(z)=\Delta$  para todo $z\in V$..

Como para todo $w\in W$ existe al menos un lado $wv$ y $W\subseteq X$ ó $W \subseteq Y$, a vertices distintos, le corresponden lados distintos, tenemos que a cada $w$ le corresponden $\Delta$ lados distintos. Entonces tenemos que:

$$
|E_W|= \Delta|W| \text{, si $W \subseteq X$ o $W \subseteq Y$}
$$

En particular si tomamos $W=X$ tendremos que $|E_X|=\Delta |X|$, pero $G$ es bipartito asi que $E_X=E=E_Y$ lo que nos dice que $\Delta|X|=\Delta |Y|$ por lo tanto $|X|=|Y|$. Esto nos dice que todo matching completo es perfecto.

Como $|X|=|Y|$, para probar que existe un matching perfecto basta probar que existe un matching completo sobre $X$, para probar esto usamos el teorema de Hall:

Sea $S\subseteq X$ y sea $l \in E_S$. Entonces existe $x\in S, y \in Y$ tal que $l$ es de la forma $l=xy$, por lo tanto $y\in \Gamma (x)\subseteq \Gamma(S)$, lo cual implica que $l\in E_{\Gamma (S)}$, como $l$  era cualquier elemento dentro de $E_s$ esto nos dice que $E_S \subseteq E_{\Gamma(S)}$,  entonces:

$$
\begin{align*}
E_S \subseteq E_{\Gamma(S)}&\Rightarrow|E_S|\leq |E_{\Gamma(S)}| \\
&\Rightarrow \Delta |S|\leq \Delta|\Gamma(S)|
\\
&\Rightarrow |S|\leq |\Gamma(S)|
\end{align*}
$$

Se satisface la condicion de Hall, entonces existe un matching completo de $X$ a $Y$.

# FIN