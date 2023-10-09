# Teorema de Hall

1. Enunciar y probar el Teorema de Hall.

---

## Teorema

Sea $G=(X\cup Y,E)$ un grafo bipartito, entonces existe un matching completo sobre $X$ si y solo para todo $S \subseteq X$ se cumple que $|S|\leq |\Gamma(S)|$.

## Prueba

Probaremos la contra-reciproca, es decir probaremos que si $G=(X\cup Y,E)$ no tiene un matching completo sobre $X$ entonces existe un $S \subseteq X$ tal que $|S|> |\Gamma(S)|$.

Como $G$ no tiene un matching completo, al correr Edmonds-Karp en el network asociado, se obtiene un corte minimal, el cual llamaremos $C$.

Sean:

- $S=X\cap C$ (los elemantos de $X$ que agrega la cola).
- $T=Y\cap C$ (los elementos de $Y$ que agrega la cola).
- $S_0$ es el conjunto de los elementos de $X$ que no tienen matching (los elementos del corte).
- $S_1,S_2,\dots,S_k$ los conjuntos de los nuevos elementos de $X$ que va agregando cada paso dentro de la iteracion final.
- $T_1,T_2,\dots,T_k$ los conjuntos de los nuevos elementos de $Y$ que va agregando cada paso dentro de la iteracion final.

Entonces por como funciona el algoritmo, tenemos:

- $S=S_0 \cup S_1 \cup \dots \cup S_k$
- $T=T_1 \cup \dots \cup T_k$         (notar que no esta $T_0)$

Sabemos que $s$ agrega a $S_0$, los de $S_0$ agregan a los de $T_1$, estos agregan a los de $S_1$, etc. Sabemos que los $T_i$ van a poder devolver a algun lado, porque si no llegarian a $t$ y no puede ser asi porque estamos en la iteracion final, entonces se cumple que $|T_i|=|S_i|$  para todo $i>0$.

**Concluison:**

$$
\begin{align*}

|\Gamma(S)|&\stackrel{(1)}{=}|T| \\

&\stackrel{(2)}{=}|T_1 \cup \dots \cup T_k| \\

&\stackrel{(3)}{=}|T_1| + \dots + |T_k|\\

&\stackrel{(4)}{=}|S_1| + \dots + |S_k|\\

&\stackrel{(5)}{=}|S_1 \cup \dots \cup S_k| \\

&\stackrel{(6)}{=}|S-S_0| \\

&<|S| \\

\end{align*}
$$

**Explicacion:**

1. El algoritmo no encontro mas elementos de $Y$ ademas de los de $T$.
2. Los $T_i$ son todos disjuntos.
3. Los $|S_i|=|T_i|$.
4. Los $S_i$ son todos disjuntos.
5. Asi definimos $S$
6. Sabemos que $S_0\neq \empty$ ya que de lo contrario se hubiera encontrado un matching completo. 

# FIN