# Las distancias no disminuyen en caminos aumentantes

1. Probar que si, dados vertices $x,z$ y flujo $f$ definimos a la distancia entre $x$ y $z$ relativa a $f$ como la longitud del menor $f$-camino aumentante entre $x$ y $z$, si es que existe tal camino, o infinito si no existe o $0$ si $x=z$, denotandola por $d_f(x, z)$ y definimos $d_k(x) = d_{fk}(s, x)$, donde $f_k$ es el $k$-esimo flujo en una corrida de Edmonds-Karp, entonces $d_k(x)\leq d_{k+1}(x)$.

---

## **Se prueba por absurdo**

Sea $A=\{y:d_{k+1}(y)<d_k(y)\}$, si el lema es cierto,  $A$ seria vacio, entonces asumimos que $A\neq\empty$ e intentamos llegar a una contradiccion.

**OBS:** $s\not \in A$, pues $d_k(s)=d_{k+1}(s)=0$ 

Como $A\neq \empty$. Tomaremos $x\in A$ tal que:  $d_{k+1}(x)=\min\{d_{k+1}(y):y\in A\}$.

******OBS:****** Como $x\in A$, entonces $d_k(x)> d_{k+1}(x)$    **( 1 )**

Como $d_{k+1}(x)<\infin$, existe un $f_{k+1}$ camino aumentante entre $s$ y $x$, de entre todos ellos, tomamos el de menor longitud. Vemos que $x\neq s$ pues $x\in A$ y  $s\not \in A$, concluimos que debe existir un vertice $z \neq x$ inmediatamente anterior a $x$ en ese camino.

### **Ahora veamos que propiedades tienen $z,x$ y lleguemos a un absurdo!**

- Como $d_{k+1}(x)$ es la menor de las distancias $d_{k+1}$ de los elementos de $A$, deducimos que cualquier elemento que tenga $d_{k+1}$ menor que $d_{k+1}(x)$ no puede estar en $A$.
- Como $z$ es el vecino inmediantamente anterior a $x$ en un $f_{k+1}$ camino aumentante, entonces $x$ es un  $f_{k+1}FF$ vecino de $z$.
- $z$ forma parte de un $f_{k+1}$ camino aumentante de menor longitud entre $s$ y $x$, el fragmento de ese camino que va de $s$ a $z$ es un $f_{k+1}$ camino aumentante de longitud minima entre $s$ y $z$.
    
    **OBS:** Como $z$ esta justo antes de $x$ concluimos que $d_{k+1}(z)=d_{k+1}(x)-1$    **( 2 )**
    
- Entonces  $d_{k+1}(z)<d_{k+1}(x)$, por lo que dijimos arriba,  $z\not \in A$, y por esto concluimos que $d_k(z)\leq d_{k+1}(z)$    **( 3 )**

### **************************************Poniendo todo junto**************************************:

$$
\begin{align*} 
d_k(x) &\stackrel{(1)}{>} d_{k+1}(x)\\ 
&\stackrel{(2)}{=} d_{k+1}(z)+1 \\
& \stackrel{(3)}{\geq} d_k(z)+1

\end{align*} 

$$

Es decir $d_k(x)>d_k(z)+1$   **( 4 )**

Esto implica que $x$ no es $f_kFF$ vecino de $z$

### **Entonces la situacion que tenemos es:**

Llegamos a que $x$ no es $f_kFF$ vecino de $z$ pero es $f_{k+1}FF$ vecino de $z$.

La unica forma en la que esto puede pasar es que el $f_k$ camino aumentante que estemos usando para construir $f_{k+1}$ sea un camino aumentante que pase primero por $x$ y luego por $z$. Expliquemos esto, para los casos que existen, los cuales son $\overrightarrow{zx} \in E$ y $\overrightarrow{xz} \in E$.

### CASO $\overrightarrow{xz} \in E$

Si $\overrightarrow{xz} \in E$, entonces:

- $x$ no es $f_kFF$ vecino de $z$, implica que $f_k(\overrightarrow{xz})=0$
- $x$ es $f_{k+1}FF$ vecino de $z$, implica que $f_{k+1}(\overrightarrow{xz})>0$

Estas dos cosas, implican que $f_{k+1}(\overrightarrow{xz})>f_k(\overrightarrow{xz})$, esto solo puede pasar si al construir $f_{k+1}$ **********ENVIAMOS********** flujo por el lado $\overrightarrow{xz}$. Por lo que el camino pasó primero por $x$ y luego por $z$.

### CASO $\overrightarrow{zx} \in E$

Si $\overrightarrow{zx} \in E$, entonces:

- $x$ no es $f_kFF$ vecino de $z$, implica que $f_k(\overrightarrow{zx})=c(\overrightarrow{zx})$
- $x$ es $f_{k+1}FF$ vecino de $z$, implica que $f_{k+1}(\overrightarrow{zx})<c(\overrightarrow{zx})$

Estas dos cosas implican que $f_{k+1}(\overrightarrow{zx})<f_k(\overrightarrow{zx})$, esto solo puede pasar si al construir $f_{k+1}$ hubo una ************************DISMINUCION************************ de flujo en el lado $\overrightarrow{zx}$ (se usó **BACKWARD)**. Para que pueda pasar esto, el camino debe haber pasado primero por $x$ y luego por $z$.

### Volviendo…

En cualquiera de los dos casos, significa que para pasar de $f_k$ a $f_{k+1}$ usamos un camino aumentante de la forma $s\dots xz\dots t$ ó $s\dots \overleftarrow{zx}\dots t$ en el caso backward, **como estamos usando Edmonds-Karp ese camino es de longitud minima.**

Por lo tanto $d_k(z)=d_k(x)+1$ **( 5 )** pero por **( 4 )** teniamos $d_k(x)>d_k(z)+1$. 

Por **( 4 )** y **( 5 )** tenemos:

$$
d_k(x)\stackrel{(4)}{>}d_k(z)+1 \stackrel{(5)}{=} (d_k(x)+1)+1
$$

Lo cual es absurdo $(d_k(x)> d_k(x)+2)$

# ******FIN******