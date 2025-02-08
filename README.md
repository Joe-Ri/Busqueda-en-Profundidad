# Búsqueda en Profundidad (DFS) 
## Enunciado del Problema

Se debe encontrar un camino desde la posición inicial `i` hasta la posición destino `e` en una cuadrícula de 6 filas por 5 columnas. El personaje puede moverse únicamente en dirección **arriba, abajo, izquierda y derecha**, pero no puede atravesar obstáculos representados en el mapa.&#x20;

### Reglas del problema:

1. Se debe seguir la estrategia de **búsqueda en profundidad (DFS)** utilizando el criterio **LIFO (Last In, First Out)**.
2. Se generan nodos en el orden **arriba, abajo, izquierda, derecha**.
3. Si un nodo explorado no tiene más movimientos posibles, se retrocede al nodo anterior.
4. La solución óptima será el camino encontrado eliminando los nodos sin salida.

## Representación Visual del Problema

### Mapa inicial con coordenadas
![Mapa con coordenadas](img/mapa_coordenadas.PNG)


## Solución Implementada

Se ha aplicado **búsqueda en profundidad (DFS)** siguiendo la estrategia **LIFO**, asegurando que en cada paso se prioricen los movimientos en el orden predefinido(arriba, abajo, izquierda, derecha). Se han utilizado estructuras de datos para **gestionar la frontera de exploración** y **almacenar los nodos explorados**.

### Tabla de búsqueda en profundidad
<div style="overflow-x: auto;">
<table style="width: 100%; border-collapse: collapse;">
  <thead>
    <tr style="background-color: #f2f2f2;">
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Paso</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Nodo actual</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Test Objetivo</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Explorados</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Posibilidades</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Frontera Anterior</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Frontera Actual (LIFO)</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Nodo siguiente</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Ruta seguida</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Ruta óptima</th>
      <th style="padding: 8px; border: 1px solid #ddd; text-align: center;">Explicación</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">1</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i(5,4)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (i): ↑(disponible)(4,4): Se le asigna (A) y se añade a la frontera ↓(disponible)(6,4): Se le asigna (B) y se añade a la frontera; ←(obstáculo); →(obstáculo)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">-</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, B]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">B</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se generan A y B y se añaden a la frontera. Se explora B (última en entrar, LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">2</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">B(6,4)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">B ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (B):↑(i)(ya explorado); ↓(fuera del mapa); ←(disponible)(6,3): Se le asigna (C) y se añade a la frontera; →(disponible)(6,5): Se le asigna (D) y se añade a la frontera;</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, B]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, C, D]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">D</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se generan C y D y se añaden a la frontera. Se explora D (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">3</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">D(6,5)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">D ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (D):↑(obstáculo)(5,3); ↓(fuera del mapa) ←(B)(ya explorado); →(fuera del mapa)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, C, D]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, C]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">C</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">D no tiene salida, se elimina. Se explora C (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">4</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">C(6,3)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">C ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (C):↑(obstáculo)(5,3); ↓(fuera del mapa) ←(disponible)(6,2): Se le asigna E y se añade a la frontera; →(B)(ya explorado)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, C]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, E]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">E</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se genera E y se añade a la frontera. Se explora E (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">5</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">E(6,2)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">E ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (E):↑(disponible)(5,2): Se le asigna (F) y se añade a la frontera; ↓(fuera del mapa); ←(disponible)(6,1): Se le asigna (G) y se añade a la frontera; →(C)(ya explorado)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, E]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, F, G]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">G</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se generan F y G y se añaden a la frontera. Se explora G (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">6</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">G(6,1)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">G ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C, E]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (G): ↑(disponible)(5,1): Se le asigna (H) y se añade a la frontera; ↓(fuera del mapa); ←(fuera de mapa); →(E)(ya explorado)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, F, ~~G~~]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, F, H]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">H</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E → G</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E → G</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se genera H y se añade a la frontera. Se explora H (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">7</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">H(5,1)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">H ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C, E, G]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (H): ↑(disponible)(4,1): Se le asigna (I) y se añade a la frontera; ↓(G)(ya explorado); ←(fuera de mapa); →(F)(asignado sin explorar) </td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, F, H]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, F, I, F]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">F</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E → G → H</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E → G → H</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se genera I y se añade a la frontera. Se explora F (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">8</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">F(5,2)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">F ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C, E, G, H]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (F):↑(obstáculo)(4,2);↓(E)(ya explorado); ←(H)(ya explorado); →(obstáculo)(5,3)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, F, I, F]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, I]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">I</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E → G → H → F</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E → G → H</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">F no tiene movimientos disponibles. Se elimina, ahora sí, de la frontera. Se explora I.</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">9</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">I(4,1)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">I ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C, E, G, H, F]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (I): ↑(disponible)(3,1): Se le asigna (J) y se añade a la frontera; ↓(H)(ya explorado); ←(fuera de mapa); →(obstáculo)(4,2)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, I]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, J]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">J</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E → G → H → F → I</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E → G → H → I</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se genera J y se añade a la frontera. Se explora J (LIFO)(único y último).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">10</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">J(3,1)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">J ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C, E, G, H, F, I]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (J):↑(disponible)(2,1): Se le asigna (K) y se añade a la frontera; ↓(I)(ya explorado); ←(fuera de mapa); →(disponible)(3,2): Se le asigna (L) y añade a la frontera;</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, J]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, L]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">L</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E → G → H → F → I → J</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E → G → H → I → J</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se genera K y L y se añaden a la frontera. Se explora L (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">11</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">L(3,2)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">L ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C, E, G, H, F, I, J]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (L): ↑(disponible)(2,2): Se le asigna (M) y se añade a la frontera; ↓(obstáculo)(4,2); ←(J)(ya explorado); →(obstáculo)(3,3)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, L]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, M]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">M</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E → G → H → F → I → J → L</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E → G → H → I → J → L</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se genera M y se añade a la frontera. Se explora M (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">12</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">M(2,2)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">M ≠ e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C, E, G, H, F, I, J, L]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">desde (M):↑(disponible)(1,2): Se le asigna (N) y se añade a la frontera; ↓(L)(ya explorado) ←(K)(asignado pero no explorado); →(disponible)(2,3): Se le asigna (O )y añade a la frontera;</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, M]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, O]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">O</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E → G → H → F → I → J → L → M</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E → G → H → I → J → L → M</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Se genera N y O y se añaden a la frontera. Se explora O (LIFO).</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">13</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">O(2,3)</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">O = e ✓</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[i, B, D, C, E, G, H, F, I, J, L, M]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Si hubiese más destinos se seguiría expandiendo.</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A, O]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">[A]</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">O</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → D → C → E → G → H → F → I → J → L → M → O/e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">i → B → C → E → G → H → I → J → L → M → e</td>
      <td style="padding: 8px; border: 1px solid #ddd; text-align: center;">Destino alcanzado. Ruta óptima encontrada.</td>
    </tr>
  </tbody>
</table>
</div>

La exploración completa se detalla en el siguiente archivo:
[🔗 Tabla de búsqueda en profundidad](tabla_de_busqueda.md)

## Representación de la Solución

### Mapa con la ruta óptima
![Mapa con la ruta óptima](img/mapa_solucion.png)


## Explicación de la Solución

1. Se inicia en el nodo `i` y se exploran los movimientos disponibles en el orden predefinido.
2. Se expanden los nodos utilizando **LIFO**, lo que implica que siempre se explorará el último nodo añadido a la frontera.
3. Cuando un nodo no tiene más movimientos disponibles, se retrocede al anterior y se sigue explorando.
4. Los nodos sin salida se eliminan en el momento en que se detectan, como en el caso del nodo `D` en el paso 3. Una vez alcanzado el destino `e`, se obtiene la ruta óptima sin los nodos descartados.

## Árbol de búsqueda generado
<p style="text-align:center;">
  <img src="img/arbol.png" alt="Árbol de búsqueda" style="display:block; margin:auto;">
</p>



Esta solución muestra la estrategia completa utilizada en DFS y cómo se ha logrado encontrar el camino correcto eliminando los nodos no útiles.

---

