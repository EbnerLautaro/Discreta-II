# Delta es igual a las columnas LD de H

1. Probar que si $H$ es matriz de chequeo de $C$, entonces:
    
    $$
    δ(C) = Min\{j : ∃ \text{ un conjunto de }j \text{ columnas }LD \text{ de } H\}
    $$
    

---

## Teorema

Sea $C$ cualquier codigo lineal con matriz de chequeo $H$, entonces:

$$
\delta (C)=\text{minimo numero de columnas linealmente dependientes de $H$}
$$

## Prueba

Denotaremos como $H^{(i)}$ a la $i$-esima columna de $H$.

Sea $M=\text{"minimo numero de columnas linealmente dependientes de $H$"}$

### Probamos $M\leq \delta(C)$:

Sea $v\neq0\in C$ con $|v|=\delta(C)=\delta$.  Entonces $v$ tiene $\delta$ unos y es la combinacion lineal de $\delta$ $e_i$, es decir, existen $j_1,\dots,j_\delta$  con $v=e_{j_1}+\dots+e_{j_\delta}$. Como $v\in C$, $H\cdot v^t=0$, tenemos entonces:

$$
\begin{align*}
0&=H\cdot v^t\\

&=H\cdot (e_{j_1}+\dots+e_{j_\delta})^t\\

&=H\cdot e_{j_1}^t+\dots+H\cdot e_{j_\delta}^t\\

&=H^{(j_1)} + \dots + H^{(j_\delta)}

\end{align*}
$$

Es decir, las columnas $j_1,\dots,j_\delta$  de $H$ forman un conjunto linealmente dependiente, entonces $M\leq\delta(C)$.

### Probamos $M\geq \delta(C)$:

Sea $\{H^{(j_1)},\dots ,H^{(j_M)}\}$ un conjunto linealmente dependiente de columnas de $H$ de tamaño minimo, entonces, existen contantes $c_r\in\{0,1\}$ no todas iguales a $0$ tales que:

$$
0=c_1H^{(j_1)}+\dots +c_MH^{(j_M)}
$$

Entonces tenemos el vector no nulo $v=c_1e_{j_1}+\dots +c_Me_{j_M}$ que pertenece al codigo, ya que:

$$
\begin{align*}
H\cdot v^t &= H (c_1e_{j_1}+\dots +c_Me_{j_M})^t\\

&=c_1He_{j_1}^t+\dots + c_MHe_{j_M}^t \\

&=c_1H^{(j_1)}+\dots +c_MH^{(j_M)}\\

&=0

\end{align*}
$$

Esto significa que $v\in C$. Concluimos que $\delta(C)\leq |v|=M$.

Probamos que  $M\geq \delta(C)\leq M$. Lo que implica que $\delta(C)=M$.

# FIN