# 3-COLOR es NP-completo

1. Probar que $3-\text{COLOR}$ es $\text{NP}$-completo.

---

## Teorema

$\text{3-COLOR}$ es $\text{NP-completo}$

## Prueba

Probaremos que $\text{3-SAT$\leq_P$3-COLOR}$, es decir, dada $B$ una expresion booleana en $CNF$ con $3$ literales por disjuncion, debemos crear un grafo $G$ tal que $\exists \vec b:B(\vec b)=1\iff \chi(G)\leq 3$.

Sea entonces $B=D_1\land \dots\land D_m$ con variables $x_1, \dots, x_n$ donde cada $D_i=l_{i1}\lor l_{i2}\lor l_{i3}$. Nuestro $G$ sera un $G_1=(V,E\cup F)$, es decir $G=(V,E)$ con lados extra $F$, determiados segun $B$. Este es $G$:

Tenemos:

- Por cada variable en la expresion booleana, un triangulo conformado por $\{t,v_j,\overline{v_j}\}$.
- Por cada disjuncion en la expresion booleana, una **garra** conformada por $\{e_{i1},e_{i2},e_{i3},a_{i1},a_{i2},a_{i3}\}$.

Ademas, hay que agregar $F$. Para definir $F$, recordamos que todo literal es una variable o negacion de una variable. Para cada literal $l$, definimos:

$$
\psi(l)= \left\{ \begin{array}{lcc}

v_k & \text{si} & l=x_k
\\
\overline {v_k} & \text{si} & l=\overline{x_k}

\end{array}
\right.
$$

Entonces definimos a $F$  como $F=\{e_{ij} \psi(l_{ij}): i \in \{1,2,\dots,m\}, j\in \{1,2,3\}\}$.

Como $G$ contiene triangulos $(K_3)$, debe ser $\chi(G) \geq 3$, asi que lo que hay que probar es que $\exists \vec b:B(\vec b)=1\iff \chi(G)=3$.

## Prueba $(\Leftarrow)$:

Vamos a probar $\chi(G)=3 \Longrightarrow \exists \vec b:B(\vec b)=1$.

Suponemos entonces que existe un coloreo propio $c$ de $G$ con tres colores. A partir de $c$ vamos a definir un $\vec b$ tal que $B(\vec b)=1$. Sea: 

$$
\vec {b_k}= \left\{ 
\begin{array}{lcc}
1 & \text{si $c(v_k)=c(s)$}\\
0 & \text{caso contrario}

\end{array}
\right.
$$

Para probar que $B(\vec b)=1$ debemos probar que $D_i(\vec b)=1, \forall D_i$. Como $\{a_{i1},a_{i2},a_{i3}\}$ forman un triangulo, entonces los $3$  colores deben aparecer entre ellos. Es decir $\exists j:c(a_{ij})=c(t)$. Ahora bien:

- $\{e_{ij},a_{ij}\}$ forman lado, por lo tanto $c(e_{ij})\neq c(a_{ij})$ y por lo tanto $c(e_{ij})\neq c(t)$.
- $\{e_{ij},s\}$ forman lado, por lo tanto $c(e_{ij})\neq c(s)$.
- $\{s,t\}$ forman lado, por lo tanto $c(s)\neq c(t)$.

Esta claro que el color de $e_{ij}$ es el tercer color, pero ademas:

- $\{e_{ij},\psi(l_{ij})\}$ forman lado, por lo tanto el color de $\psi(l_{ij})$ no es el tercer color.
- $\{\psi(l_{ij}), t\}$ forman lado, por lo tanto el color de $c(\psi(l_{ij}))\neq c(t)$.

En consecuencia $c(\psi(l_{ij}))=c(s)$.

- Si $\psi(l_{ij})=v_k$ (porque $l_{ij}=x_k$) entonces tenemos que $c(v_k)=c(s)\Rightarrow b_k=1$ (por la definicion de $\vec b)$ y $l_{ij}(\vec b)=1\Rightarrow D_i(\vec b)=1$.
- Si en cambio Si $\psi(l_{ij})=\overline{v_k}$  (porque $l_{ij}=\overline{x_k}$)  entonces, como $\{v_k,\overline{v_k}\}$ forman lado $c(v_k)\neq c(\overline{v_k})$, debe ser que $c(v_k)\neq c(s) \Rightarrow b_k=0$. Pero $l_{ij}= \overline {x_k}\Rightarrow l_{ij}(\vec b)= \overline{b_k}=1$  y $D_i(\vec b)=1$.

Como en cualquiera de los dos casos concluimos que $D_i(\vec b)=1$, debe ser que $B(\vec b)=1$.

## Prueba $(\Rightarrow)$:

Asumimos que $\exists \vec b : B(\vec b)=1$ y construimos un coloreo con $3$ colores.

Definimos el siguiente coloreo:

$$
c(s)=C_1\\
c(t)=C_2\\
c(v_k)= \left \{ 
\begin{array}{lcc}
C_1 & \text{si } b_k=1\\
C_0 & \text{si } b_k=0\\
\end{array} \right.\\

c(\overline{v_k})= \left \{ 
\begin{array}{lcc}
C_0 & \text{si } b_k=1\\
C_1 & \text{si } b_k=0\\
\end{array} \right.

$$

Vemos que ni $\{s,t\}$, $\{v_k,t\}$ y $\{\overline{v_k},t\}$ no crean problemas. 

Para colorear las garras, vemos primero como colorear los $e_{ij}$. Como $\exists \vec b : B(\vec b)=1, \forall i \in\{1,2,\dots,n\} \ D_i(\vec b)=1$, es decir, para cada $i$ dado, existe un $j$ tal que $l_{ij}(\vec b)=1$. Tomamos el primer $j$ tal que $l_{ij}(\vec b)=1$ y definimos:

$$
c(e_{ir})=\left \{ 
\begin{array}{lcc}
C_0 & \text{si } r=j\\
C_2 & \text{si } r\neq j\\
\end{array} \right.

$$

Con este coloreo, $\{e_{ir},s\}$ no crea problemas. Ademas:

- Para $r\neq j$ tenemos que $\{e_{ir},\psi(e_{ir})\}$ no crea problemas, ya que $c(e_{ir})=C_2$ y $c(\psi(e_{ir}))=C_1\lor C_0$, este lado no causa problemas.
- Para $r= j$ tenemos que $c(e_{ir})=C_0$ y para ver que $\{e_{ir},\psi(e_{ir})\}$ no causa problemas, debemos analizar dos casos:
    - Si $l_{ij}=x_k$, entonces $\psi(e_{ir})=v_k$ y como $l_{ij}(\vec b)=1$, debe ser $x_k=1$ y por lo tanto $c(v_k)=C_1$. En este caso no crea problemas
    - Si $l_{ij}=\overline{x_k}$, entonces $\psi(e_{ir})=\overline{v_k}$ y como $l_{ij}(\vec b)=1$, debe ser $x_k=0$ y por lo tanto $c(\overline{v_k})=C_1$. En este caso tampoco crea problemas.

Finalmente solo resta colorear los $a_{ij}$:

$$
c(a_{ir})=\left \{ 
\begin{array}{lcc}
C_2 & \text{si } r=j\\
C_1 \lor C_0 &\text{si } r\neq j\\

\end{array} \right.

$$

Es decir, coloramos con $C_2$ al $a_{ij}$ y los otros dos, uno con $C_1$ y otro con $C_0$ de modo que:

- El triangulo $\{a_{i1},a_{i2},a_{i3}\}$ no crea problemas.
- El lado $\{a_{ij},e_{ij}\}$ no crea problemas, ya que $c(a_{ij})=C_2$ y $c(e_{ij})=C_0$.
- El lado $\{a_{ir},e_{ir}\}$ con $r\neq j$ no crea problemas, ya que  $c(a_{ir})=C_1\lor C_0$ y $c(e_{ir})=C_2$.

# FIN

Cambiamos todas las $w_k$ por $\overline{v_k}$, los $b_{ij}$ por $a_{ij}$ y los $u_{ij}$ por $e_{ij}$.