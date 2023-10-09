# G bipartito ⇒ χ’(G)=Δ

1. Probar que si $G$  es bipartito entonces $\chi'(G)=\Delta$.

---

## Definicion

El indice cromatico de un grafo es la menor cantidad de colores de un coloreo propio de los LADOS, se denota por $\chi'(G)$.

## Teorema

Si $G$ es bipartito, entonces $\chi'(G)=\Delta$.

## Prueba

Sea $H$ bipartito regular, con $\Delta (H)=\Delta (G)$ tal que $G\subseteq H$. Como $H$ es bipartito regular, por el teorema del matrimonio, sabemos que tiene un matching perfecto, el cual llamaremos $M$.

Sea $H_2=(V(H),E(H)-E(M))$. Como $M$ es matching perfecto, $H_2$ sigue siendo regular y $|H_2|=\Delta(H)-1$. Como $H_2$ es bipartito regular, tiene un matching perfecto, llamemosle $M_2$. Si lo removemos, nos vuelve a quedar un grafo bipartito regular con $\Delta = \Delta(H)-2$. Podemos continuar removiendo lados $\Delta$ veces.

Tenemos entonces matchings perfectos $M, M_1,\dots,M_\Delta$ con $E(H)=E(M_1)\cup \dots \cup E(M_\Delta)$.

Damos entonces el coloreo $C(xy)=i \text{ si, } xy\in E(M_i)$.

Este coloreo es propio, pues $M_i$ es matching y utiliza solo $\Delta$ colores. 

Ahora falta probar que existe $H$, es decir, que para todo $G$ bipartito existe un $H$ bipartito regular tal que $\Delta(H)=\Delta(G)$ y $G\subseteq H$.

La idea es ir construyendo grafos cada vez mas grandes tal que el $\delta$ crezca, pero el $\Delta$ se mantenga igual, terminando eventualmente con un grafo con $\delta=\Delta$, es decir, un grafo regular.

Para esto basta probar que existe $\tilde G$ con $G\subseteq G$ tal que $\tilde G$ es bipartito con $\Delta(G)=\Delta(\tilde G)$ y $\delta(G)=\delta(\tilde G)+1$.

Sea $G=(V=X\cup Y,E)$ bipartito y sea $G°=(V°,E°)$  una copia exacta de $G$.

Definimos $\tilde G=(\tilde V, \tilde E)$ donde:

- $\tilde V =V\cup V°$
- $\tilde E = E \cup E° \cup E^*$
- $E^*=\{ vv°:d_G(v)<\Delta(G) \}$

Hacemos las siguientes observaciones de $\tilde G$:

1. $\tilde G$  es bipartito, sus partes son $X \cup Y°$ y $X° \cup Y$. No hay lados de $X$ a $X$, ni lados de $Y°$  a $Y°$ , ni lados de $X$ a $Y°$, etc.
2. Sea $v\in V$ tal que $d_G(v)=\Delta$, entonces $v$ no es parte de ningun lado de $E^*$, tampoco $v°$, por lo que $d_{\tilde G}(v)=d_{\tilde G}(v°)=\Delta$.
3. Sea $v\in V$ tal que $d_G(v)<\Delta$, entonces $v$ forma parte de un lado de $E^*$, tambien $v°$, por lo que $d_{\tilde G}(v)=d_{\tilde G}(v°)=\Delta +1$.

Entonces:

$$
\Delta(\tilde G)=\Delta (G)\\
\delta(\tilde G)=\delta (G)+1
$$

Si iteramos el procedimiento tenemos:

$$
G\rightarrow \tilde{G}

\rightarrow \tilde{\tilde{G}\,} 

\rightarrow \tilde{\tilde{\tilde{G}\,}}

\rightarrow \dots 
$$

LLegaremos a un grafo $H$ bipartito tal que $\delta(H)=\Delta(H)=\Delta$

# FIN