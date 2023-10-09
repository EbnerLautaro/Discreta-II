# Demostaraciones Discreta

1. Complejidad del algoritmo de Edmonds-Karp
    - Nota: en la prueba se definen unas distancias, y se prueba que esas distancias no disminuyen en pasos sucesivos de EK. Ud. puede usar esto sin necesidad de probarlo
    
    [Complejidad de Edmonds-Karp](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Complejidad%20de%20Edmonds-Karp%201a5e27dd4c0e4a5cbae17e24f8c35913.md)
    
2. Probar que si, dados vertices $x,z$ y flujo $f$ definimos a la distancia entre $x$ y $z$ relativa a $f$ como la longitud del menor $f$-camino aumentante entre $x$ y $z$, si es que existe tal camino, o infinito si no existe o $0$ si $x=z$, denotandola por $d_f(x, z)$ y definimos $d_k(x) = d_{fk}(s, x)$, donde $f_k$ es el $k$-esimo flujo en una corrida de Edmonds-Karp, entonces $d_k(x)\leq d_{k+1}(x)$
    
    [Las distancias no disminuyen en caminos aumentantes](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Las%20distancias%20no%20disminuyen%20en%20caminos%20aumentante%2020a77f5bccb743a18601dbfb4a3c2ceb.md)
    
3. ¿Cual es la complejidad del algoritmo de Dinic? 
    
    [Complejidad del algoritmo de Dinic](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Complejidad%20del%20algoritmo%20de%20Dinic%20e0aff13f76a74b11ac0b07bfdd5a1738.md)
    
4. ¿Cual es la complejidad del algoritmo de Wave? 
    
    [Complejidad de Wave](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Complejidad%20de%20Wave%2001bd1877938f40098095a806f3f416b9.md)
    
5. Probar que la distancia en networks auxiliares sucesivos aumenta.
    
    [La distancia en NA sucesivos aumenta](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/La%20distancia%20en%20NA%20sucesivos%20aumenta%204a1213c4e53049e69982c5085e4dc2a4.md)
    
6. Probar que el valor de todo flujo es menor o igual que la capacidad de todo corte y que si  $f$ es un flujo, entonces las siguientes afirmaciones son equivalentes:
    1. $f$ es maximal.
    2. Existe un corte $S$  tal que $v(f) = cap(S)$. (y en este caso, $S$ es minimal)
    3. No existen $f$-caminos aumentantes.
    
    [Max-flow Min-Cut](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Max-flow%20Min-Cut%20d9702a9abda84975b3613ec889098111.md)
    
7. Probar que $2-\text{COLOR}$  es polinomial.
    
    [2-COLOR es polinomial ](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/2-COLOR%20es%20polinomial%2086d7ecaf65424b668dbcdc33c86af885.md)
    
8. Enunciar y probar el Teorema de Hall.
    
    [Teorema de Hall](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Teorema%20de%20Hall%20bf0ec86ff4404e43a10b92d3876bb60a.md)
    
9. Enunciar y probar el teorema del matrimonio de Konig.
    
    [Teorema del matrimonio de Konig](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Teorema%20del%20matrimonio%20de%20Konig%209d8ba5f1c8054ed0b7689bf5bc621a88.md)
    
10. Probar que si $G$ es bipartito entonces $\chi'(G)=\Delta$
    
    [G bipartito ⇒ χ’(G)=Δ](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/G%20bipartito%20%E2%87%92%20%CF%87%E2%80%99(G)=%CE%94%2004446553e70f4373892afa9feca4374d.md)
    
11. Probar la complejidad $O(n^4)$ del algoritmo Hungaro y dar una idea de como se la puede reducir a $O(n³)$.
    
    [Complejidad Hungaro](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Complejidad%20Hungaro%2084b012bc00a84148a7ee19c25dc366e8.md)
    
12. Enunciar el teorema de la cota de Hamming y probarlo. 
    
    [Cota de Hamming](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Cota%20de%20Hamming%206ecbd555a2b94868b9f344abde595a02.md)
    
13. Probar que si $H$ es matriz de chequeo de $C$, entonces:
    
    $$
    δ(C) = Min\{j : ∃ \text{ un conjunto de }j \text{ columnas }LD \text{ de } H\}
    $$
    
    [Delta es igual a las columnas LD de H](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Delta%20es%20igual%20a%20las%20columnas%20LD%20de%20H%20e5737f153049432ebef55fe868b2e600.md)
    
14. Sea $C$ un codigo ciclico de dimension $k$ y longitud $n$ y sea $g(x)$ su polinomio generador. Probar que:
    1. $C$ esta formado por los multiplos de $g(x)$ de grado menor que $n$: 
        
        $$
        C = \{ p(x) : gr(p) < n \land g(x) \mid p(x)\}
        $$
        
    2. $C=\{v(x) \odot g(x): v(x) \text{es un polinomio cualquiera}\}$
    3.  $gr(g(x)) = n − k$
    4. $g(x) \mid (1+x^n)$
    
    [Propiedades de g(x)](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/Propiedades%20de%20g(x)%206fd73c521b5c437f984839d7451ca5f7.md)
    
15. Probar que $3-\text{SAT}$ es $\text{NP}$-completo.
    
    [3-SAT es NP-completo.](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/3-SAT%20es%20NP-completo%2081b47011eb1e49faaf37519cfd5bd249.md)
    
16. Probar que $3-\text{COLOR}$ es $\text{NP}$-completo.
    
    [3-COLOR es NP-completo](Demostaraciones%20Discreta%20fc71bb96a295471c90ec34b000331083/3-COLOR%20es%20NP-completo%20d6f09b267b8b469ca5919acd9b767a4d.md)