# La distancia en NA sucesivos aumenta

1. Probar que la distancia en networks auxiliares sucesivos aumenta.

---

## Teorema

La distancia entre $s$ y $t$ en Networks Auxiliares consecutivos aumenta.

## Prueba

- Sea $A$ un network auxiliar y  $A'$ el network auxiliar siguiente.
- Sea $d(x)=d_f(s,x)$ y $d'(x)=d_{f'}(s,x)$.

Sabemos que $d(t)\leq d'(t)$ por la prueba de Edmonds-Karp, queremos probar que vale el $<$.

Sea $s=x_0,\dots,x_r=t$ un camino dirigido en $A'$, sabemos que este camino no existe en $A$, porque para pasar de $A$ a $A'$ bloqueamos todos los caminos dirigidos de $s$ a $t$ que existian en $A$, por lo tanto, si ese camino hubiese estado en $A$, Dinic lo hubiese bloqueado y por ende no estaria en $A'$. Veamos cuales son las razones por las cuales no estaria en $A$:

- **CASO 1:** Falta un vertice.
- **CASO 2:** Falta un lado.

### CASO 1 (falta un vertice)

Como $t$ esta en $A$, sabemos que $x_i \neq t$, recordemos tambien, que todos los vertices distintos de $t$ que esten a distancia mayor o igual que $t$ no se incluyen en $A$, concluimos que $x_i$ no esta en $A$ porque $d(t)\leq d(x_i)$, por Edmonds-Karp, tenemos que $d(x_i)\leq d'(x_i)$. Como $s=x_0,\dots,x_r=t$ es un camino en $A'$ y $A'$ es un Network por niveles, concluimos que $d(x_i)=i$ para todo $i$ entre $0$  y $r$, como $x_i\neq t$ entonces $i<r$. Juntando todo tenemos:

$$
\begin{align*}

d(t)&\leq d(x_i) & \text{porque no esta en A}\\
&\leq d'(x_i) & \text{Edmonds-Karp}\\
&=i<r=d'(t) & x_i \neq t
\end{align*}
$$

## Caso 2 (falta un lado)

Asumimos ahora que estan todos los $x_i$ en $A$ pero falta algun lado $\overrightarrow{x_ix_{i+1}}$, tomamos el primer $i$ para el cual pasa esto, por Edmonds-Karp sabemos que $d(x_{i+1})\leq d'(x_{i+1})$ entonces tenemos dos subcasos, menor o igual, veamos:

### Caso $d(x_{i+1})< d'(x_{i+1})$:

Por Edmonds-Karp sabemos que $b(x)\leq b'(x)$ y $d(t)=d(x)+b(x)$ para cualquier $x$, entonces:

$$
\begin{align*}

d(t)&= d(x_{i+1})+b(x_{i+1}) & \\
&\leq d(x_{i+1})+b'(x_{i+1}) &  \text{Edmonds-Karp}\\
&< d'(x_{i+1})+b'(x_{i+1}) &\text{Hipotesis}\\
& =d'(t)

\end{align*}
$$

### Caso $d(x_{i+1})=d'(x_{i+1})$:

Si este fuera el caso, tenemos que $x_i$ y $x_{i+1}$están en niveles consecutivos, pero no existe el lado $\overrightarrow{x_ix_{i+1}}$. 

Deducimos entonces que el lado $\overrightarrow{x_ix_{i+1}}$ representa un **lado forward saturado** del network original o un **lado backward vacío** . Sabemos entonces que la única forma de que este lado esté presente en $A'$, es que durante la construcción de $f'$, usemos un lado $\overrightarrow{x_{i+1}x_i}$, pero tampoco puede existir en 
$A$, porque no sería legal dados los niveles. Por lo tanto queda descartado el caso donde $d(x_{i+1}) = d'(x_{i+1})$.

# FIN