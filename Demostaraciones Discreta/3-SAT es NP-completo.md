# 3-SAT es NP-completo.

1. Probar que $3-\text{SAT}$ es $\text{NP}$-completo.

---

## Teorema

$\text{3-SAT}$ es $\text{NP-completo}$.

## Prueba

Veamos que $\text{SAT} \leq_P \text{3-SAT}$.

Sea $B=D_1\land\dots\land D_m$ una instancia de $\text{CNF-SAT}$, con variables $x_1,\dots,x_n$ con $D_i=l_{i1}\lor \dots \lor l_{ik_i}$ ($k_i$ es la cantidad de variables que estan en $D_i$) donde $l_{ij}$ son literales. Para cada $D_i$ construiremos en tiempo polinomial un $E_i$ que sea conjuncion de $3$ literales. De modo que $\tilde B=E_1\land \dots\land E_m$ sera nuestra instancia de $\text{3-SAT}$. Para realizar esta construccion vamos a proceder de diferente manera segun la cantidad de literales presentes en cada $D_i$. 

Vamos a omitir escribir los subindices, ya que siempre estamos hablando del $i$-esimo $D$.

- Si $k=3$: Definimos
    
    $$
    E=D
    $$
    
- Si $k=2$: Definimos una variable extra llamada $y_{i1}$, y definimos:
    
    $$
    E_i=(l_{1}\lor l_{2}\lor y_{1})\land (l_{1}\lor l_{2}\lor \overline {y_{1}})
    $$
    
- Si $k=1$: Tomamos dos variables extras $y_{i1},y_{i2}$ y definimos:
    
    $$
    E=
    
    (l_{1}\lor y_{1}\lor y_{2})\land 
    
    (l_{1}\lor y_{1} \lor\overline{ y_{2}})\land 
    
    (l_{1}\lor \overline{y_{1}}\lor y_{2})\land 
    
    (l_{1}\lor \overline {y_{1}}\lor \overline{y_{2}}) 
    
    $$
    
- Si $k>3$: Agregamos $k_i-3$ variables nuevas y definimos:
    
    $$
    E = (l_1 \lor l_2 \lor y_1) \land (l_3 \lor \overline{y_1} \lor y_2) \dots (l_{k-2} \lor \overline{y_{k-4}} \lor y_{k-3}) \land (l_{k-1} \lor l_{k} \lor \overline{y_{k-3}})
    $$
    
    Para entender mejor, ver los intermedios y los extremos: 
    
    - Los intermedios tienen un literal y 2 variables nuevas.
    - Los extremos tienen 2 literales y una variable nueva.

Ahora tenemos que probar que:

$$
\exist \vec b : B(\vec b )=1 

\iff 

\exist\vec a:\tilde B(\vec b, \vec a)=1 
$$

Es decir, que si $B$ es satisfacible mediante una asignacion de sus variables $\vec b$, entonces $\tilde B$ es satisfacible mediante una ampliacion de dicha asignacion (para abarcar a las nuevas variables).

## Prueba $(\Leftarrow)$:

Vamos a probar $\exist\vec a:\tilde B(\vec b, \vec a)=1 
\Longrightarrow
\exist \vec b : B(\vec b )=1$ 

.

Sabemos que $\tilde B(\vec b,\vec a)=1$, debemos ver que $B(\vec b) =1$. Supongamos, para llegar a un absurdo que $B(\vec b)= 0$ entonces existe un $i$ tal que $D_i=0$. Pero sabemos que $E_i(\vec b, \vec a)=1,\forall i$, analicemos como se construyo $E_i$:

- Si $k=3$, $D_i(\vec b)=0 \Longrightarrow E_i=0 \Longrightarrow \tilde B(\vec b, \vec a)=0$, lo cual es absurdo.
- Si $k=2,D_i=l_1(\vec b)\lor l_2(\vec b)=0 \Longrightarrow E_i= a_1\land \overline {a_1}=1$, lo cual es absurdo
- Si $k=1, D_i=l_1(\vec b)=0\Longrightarrow 
(a_1\lor a_2)\land
(a_1\lor \overline{a_2})\land
(\overline{a_1}\lor a_2)\land
(\overline{a_1}\lor \overline{a_2}) = 1$, lo cual es absurdo.
- Si $k>3,D_i(\vec b)=0\Longrightarrow l_j(\vec b)=0,\forall j.$ Es decir, podemos ignorar los literales $l_j$. Pero como $\tilde B(\vec b,\vec a )=1$, debe ser cierto que $1=a_1
\land (\overline{a_1}\lor {a_2})
\land (\overline{a_2}\lor {a_3})

\land \dots
\land (\overline{a_{k_{i-1}-4}}\lor {a_{k_i-3}})

\land \overline{a_{k_{i-1}-3}}$, o dicho de otro modo,  $1=a_1
\land ({a_1}\Rightarrow {a_2})
\land ({a_2}\Rightarrow {a_3})

\land \dots
\land ({a_{k_{i-1}-4}}\Rightarrow {a_{k_i-3}})

\land \overline{a_{k_{i-1}-3}}$, lo cual es absurdo.

En cualquier caso llegamos a una contradiccion, luego, debe ser que $B(\vec b)=1$.

## Prueba $(\Rightarrow)$:

Vamos a probar $\exist \vec b : B(\vec b )=1 

\Longrightarrow

\exist\vec a:\tilde B(\vec b, \vec a)=1$ .

Supongamos que $B(\vec b)=1$. 

- Para los $k_i=1$ y $k_i=2$ basta ver que definiendo $a_j=0,D_i(\vec b)\Rightarrow E_i(\vec b, \vec a)=1$.
- Veamos para $k>3$. $D_i(\vec b)=1\Rightarrow\exists j :l_j(\vec b)=1$, entonces definimos:
    - $a_1=a_2=\dots=a_{j-2}=1$
    - $a_{j-1}=a_j=\dots=a_{k-3}=0$
    
    Asi obtenemos:
    
    $$
    \begin{align*}
    E(\vec b,\vec a)&= (l_1(\vec b)\lor l_2(\vec b) \lor a_1) &\text{ es 1 por $a_1$}\\
    
    &\land (l_3(\vec b)\lor \overline {a_1} \lor a_2) &\text{es 1 por $a_2$}\\
    
    &\,\ \vdots\\
    
    &\land (l_{j-1}(\vec b)\lor \overline {a_{j-3}} \lor a_{j-2}) &\text{es 1 por $a_{j-2}$}\\
    
    &\land (l_{j}(\vec b)\lor \overline {a_{j-2}} \lor a_{j-1}) &\text{es 1 por $l_j$}\\
    
    &\land (l_{j+1}(\vec b)\lor \overline {a_{j-1}} \lor a_{j}) &\text{es 1 por $\overline{a_{j-1}}$}\\
    
    &\land \vdots \\
    
    &\land (l_{k-1}(\vec b)\lor l_{k} \lor \overline {a_{k_i}}) &\text{es 1 por $\overline{a_{k_i}}$}\\
    
    &=1
    \end{align*}
    $$
    
    Concluimos que en este caso $E(\vec b,\vec a)=1$. 
    

# FIN