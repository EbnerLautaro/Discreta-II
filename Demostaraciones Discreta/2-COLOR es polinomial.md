# 2-COLOR es polinomial

1. Probar que $2-\text{COLOR}$  es polinomial.

---

## Teorema

$\text{2-COLOR}$  es polinomial.

## Prueba

Para ver que $\text{2-COLOR}$  es polinomial, basta con dar un algoritmo polinomial que determine si $\chi (G)\leq 2$ para el caso de $G$  conexo. Daremos el siguiente algoritmo:

1. Elegir un vertice $x$ cualquiera.
2. Correr  $BFS(x)$, con el que creamos un arbol.
3. Para cada vertice $z$, sea $N(z)$ el nivel de $z$ en el arbol $BFS(x)$.
4. Colorear $c(z)=N(z)\,\ mod\,\ 2$
.
5. Chequear si el coloreo dado es propio.
    1. Si lo es retornar $\chi(G)\leq 2$.
    2. Si no lo es retornar $\chi (G)>2$.

Queda probar que es de orden polinomial y que es correcto. 

## Orden polinomial

Crear $BFS(x)$ es $O(m)$, los niveles y el coloreo asociado, se hacen al mismo tiempo que el $BFS(x)$, si un vertice $u$ que esta en el arbol agrega a un vertice $v$ que no esta, coloreamos a $v$ con $1$ si $c(u)=0$ y con $0$ si $c(u)=1$.

Chequear si un coloreo es propio es $O(m)$. 

Entonces la complejidad total es $O(m)+O(m)=O(m)$

## Correctitud:

Obviamente si el algoritmo retorna $"\chi(G)\leq 2"$ es correcto, pues solo devuelve esa respuesta si el coloreo con 2 colores es propio. 

Queda probar que la respuesta $"\chi(G)> 2"$ sea correcta, basicamente probar que no existe ningun coloreo con 2 colores.

Supongamos que el coloreo no es propio, eso implica que existen $z,y$ distintos tales que $c(z)=c(y)$ pero $zy$  es un lado en $G$.

Sea $x=z_o,z_1\dots z_k=z$ el unico camino entre $x$ y $z$ en el arbol $BFS$ y sea $x=y_o,y_1\dots y_j=y$ el unico camino entre $x$ e $y$ en el arbol $BFS$. 

Observamos que $k=N(z)\land j=N(y)$, por lo que nuestro algoritmo los colorea de la forma $c(z)=(k\,\ mod\,\ 2) 
\land c(y)=(j\,\ mod\,\ 2)$. Como $c(z)=c(y)$ por hipotesis, concluimos que $(k\,\ mod\,\ 2)=(j\,\ mod\,\ 2)$, es decir, tienen la misma paridad.

Estos dos caminos, comienzan con $x$ pero terminan distinto, entonces existe un ultimo vertice en comun entre estos, llamemosle $w$, entonces existe $p$ tal que  $z_0=y_0, z_1=y_1\dots z_p=y_p=w$ teniendo en cuenta que $zy$ es un lado en $G$ y que $z_k=z,y_j=y$, entonces tenemos el ciclo:

$$
w\ z_{p+1}\ z_{p+2}\ \dots\ z_{k-1}\ z\ y\ y_{j-1}\ y_{j-2}\ \dots\  y_{p+1}\ w
$$

Veamos cuantos vertices hay en ese ciclo:

- $w$ suma 1.
- Los $z_{p+1}\,\ z_{p+2} \,\ \dots \,\ z_{k-1}$ son $k-p$.
- Los $y_{j-1}\,\ y_{j-2}\,\ \dots\,\  y_{p+1}$ son $j-p$.

Entonces el total es $1+(k-p)+(j-p)=k+j-2p+1$.

Antes vimos que $k$ y $j$ tienen la misma paridad, por lo que su suma es **PAR**. Vemos tambien que $2p$ es ********PAR********. Concluimos que la cantidad de vertices en el ciclo es $\text{PAR - PAR + $1$}$ esto es obviamente impar, lo que implica que $G$ tiene adentro un ciclo impar, por lo que $\chi(g)\geq 3>2$ y la respuesta del algoritmo es correcta.

# FIN