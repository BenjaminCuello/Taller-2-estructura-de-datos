# Integrantes
Benjamín Cuello, 21.682.135-1, benjamin.cuello@alumnos.ucn.cl, Paralelo C1 

Benjamín Salas, 21.758.667-4, benjamin.salas02@alumnos.ucn.cl, Paralelo C2
# Implementación del Algoritmo Minimax con Poda Alfa-Beta en un Juego

El proyecto trata sobre la aplicacion del algoritmo `Minimax` con `Poda Alfa-Beta` para crear un agente inteligente que tome las decisiones más optimas, utilizando el juego `Gato` tambien conocido como `Tres en linea` o `Tic-Tac-Toe`.

## **Minimax**
El algoritmo `Minimax` permite tomar decisiones óptimas en juegos de dos jugadores de suma cero. Su objetivo principal es minimizar la pérdida máxima que un jugador puede sufrir, asumiendo que el oponente juega de manera óptima.

### **Funcionamiento:**
1. El árbol de decisiones del juego se representa como un conjunto de estados (nodos) y movimientos posibles (ramas).
2. Los jugadores alternan turnos:
   - **Maximización:** Trata de maximizar la puntuación.
   - **Minimización:** Trata de minimizar la puntuación.
3. Se evalúan los valores de los nodos hoja utilizando una función de utilidad.
4. Se realiza un recorrido **de abajo hacia arriba** en el árbol:
   - Los nodos **Max** toman el valor máximo de sus hijos.
   - Los nodos **Min** toman el valor mínimo de sus hijos.

## **Poda Alfa-Beta**

La **Poda Alfa-Beta** es una mejora del algoritmo Minimax que reduce el número de nodos evaluados sin alterar el resultado final.

### **Funcionamiento:**
1. Utiliza dos límites:
   - **Alfa (α):** El mejor valor que el maximizador puede garantizar.
   - **Beta (β):** El mejor valor que el minimizador puede garantizar.
2. **Poda:** Si un nodo genera un valor que no afecta el resultado, se deja de explorar esa rama.

## **Explicación teórica**

### **Minimax**
1. **Objetivo:** Maximizar la ganancia del jugador mientras se minimiza la pérdida causada por el oponente.
2. **Funcionamiento:**
   - Representa el juego como un árbol de decisiones.
   - Los nodos hoja tienen valores calculados por una función de utilidad (evaluación del estado).
   - Se recorre el árbol **de abajo hacia arriba**, alternando entre los jugadores:
     - **Max:** Escoge el valor máximo de los hijos.
     - **Min:** Escoge el valor mínimo de los hijos.

### **Poda Alfa-Beta**
1. **Optimización:** Reduce la cantidad de nodos evaluados.
2. **Límites:**
   - **Alfa (α):** Mejor resultado garantizado para el maximizador.
   - **Beta (β):** Mejor resultado garantizado para el minimizador.
3. **Poda:** Si un nodo no mejora el resultado, se deja de evaluar.

## **Análisis de complejidad**

### **Sin poda alfa-beta (Minimax):**
La complejidad temporal es \(O(b^d)\), donde:
- **\(b\):** Número de movimientos posibles en cada turno.
- **\(d\):** Profundidad del árbol (número de turnos hasta el final).

Para el Tic-Tac-Toe:
- **\(b \leq 9\)** (máximo número de espacios libres).
- **\(d \leq 9\)** (máximo número de turnos).

En el peor caso, el algoritmo evaluaría \(9^9 = 387,420,489\) nodos.

### **Con poda alfa-beta:**
En el mejor caso (cuando se evalúan primero las ramas más prometedoras), la complejidad se reduce a \(O(b^{d/2})\). 

Para el Tic-Tac-Toe:
- La evaluación máxima sería \(9^{9/2} \approx 31,623\) nodos.

**Comparación:**
| **Estrategia**   | **Complejidad** | **Nodos evaluados** (aprox.) |
|-------------------|-----------------|-----------------------------|
| Minimax           | \(O(b^d)\)     | 387,420,489                 |
| Poda Alfa-Beta    | \(O(b^{d/2})\) | 31,623                      |


## Estructura del Código

- **Lenguaje de Programación:** C++
- **Compilador:** g++
- **Estructura del Código:**
    - El código está organizado en múltiples archivos `.cpp` y `.h` para mantener una estructura modular y escalable.
    - Uso de punteros y arrays estáticos para la gestión de la memoria dinámica.

## Ejecución del Programa

Para compilar y ejecutar el programa, utiliza los siguientes comandos:

- **Compilar:** PONER AL FINAL AQUI
- **Ejecutar:** AQUI TAMBIEN
