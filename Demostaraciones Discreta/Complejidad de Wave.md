# Complejidad de Wave

1. ¿Cual es la complejidad del algoritmo de Wave? 
    - No hace falta probar que la distancia en networks auxiliares sucesivos aumenta.

---

## Teorema

La complejidad de los algoritmos de Wave  $O(n^3)$.

### Demostracion

La complejidad del paso bloqueante de Wave esta dada por:

$$
S+P+V+Q
$$

Donde:

- $S=$ cantidad de veces que enviamos de un $x$ a un $y$ y lo saturamos.
- $P=$ cantidad de veces que enviamos de un $x$ a un $y$ y no lo saturamos.
- $V=$ cantidad de veces que enviamos de un $x$ a un $y$ y lo vaciamos.
- $Q=$ cantidad de veces que enviamos de un $x$ a un $y$  y no lo vaciamos.

Veamos las complejidades de cada una de las cosas por separado.

### Cantidad de Olas

Cuando hacemos una ola hacia adelante, bloqueamos un vertice, de no ser el caso seria la ultima ola. Por lo tanto hay $O(n)$ olas hacia adelante.

Solo podemos hacer una ola hacia atras luego de hacer una ola hacia adelante, por lo que hay $O(n)$ olas hacia atras.

### Complejidad de $S$

Para $S$, sabemos que $\text{forward\_balance}$ elimina al lado $xy$ luego de enviarle flujo si lo hemos saturado. Si en algun momento se vaciara por un $\text{backward\_balance}$ desde $y$, entonces $y$ estaria bloqueado y tampoco habria que enviarle nada por ese lado. Concluimos que $O(S)=O(m)$.

### Complejidad de $V$

Para $V$, sabemos que $\text{backward\_balance}$ elimina al lado $xy$ luego de devolverle flujo, ya que $x$ esta bloqueado y nadie le va a volver a mandar por la misma razon. Concluimos que $O(V)=O(m)$.

### Complejidad de $P$

Para $P$, cuando hacemos $\text{forward\_balance}$  solo el ultimo lado que vemos es capaz de enviar y no saturar, entonces, esto pasa una vez por cada $\text{forward\_balance}$ , por lo tanto $O(P)=O(1)\cdot \# \text{forward\_balance}$. Sabemos que hay que hay a lo sumo $(n-2)$ $\text{forward\_balance}$  (porque no contamos a $s$ ni $t$) por ola entonces $O(P)=O(n-2)\cdot O(n)=O(n^2)$. El ultimo termino es la cantidad de olas hacia adelante.

### Complejidad de $Q$

Cuando haces un $\text{backward\_balance}$, solo el ultimo lado que miramos es capaz de no ser vaciado y por lo tanto hay a lo sumo uno por ola hacia atras por vertice, concluimos que $O(Q)=O(n)\cdot O(n) = O(n^2)$.

### Conclusion

La complejidad del paso bloqueante de Wave esta dada por:

$$
\begin{align*}

S+P+V+Q &= \\

O(m)+O(n^2)+O(m)+O(n^2) &= \\

O(n^2)
\end{align*}
$$

## Complejidad de Wave

Acabamos de probar que la complejidad del paso bloqueante de Wave es de complejidad $O(n^2)$. Como a lo sumo hay $n$ networks auxiliares, dado que las distancias en networks auxiliares susesivos aumentan, entonces  la complejidad total de Wave es de $O(n)\cdot O(n^2)=O(n^3)$.