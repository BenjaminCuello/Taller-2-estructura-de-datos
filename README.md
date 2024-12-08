# Integrantes
Benjamín Cuello, 21.682.135-1, benjamin.cuello@alumnos.ucn.cl, Paralelo C1 

Benjamín Salas, 21.758.667-4, benjamin.salas02@alumnos.ucn.cl, Paralelo C2
# Implementación del Algoritmo Minimax con Poda Alfa-Beta en un Juego
El proyecto trata sobre una aplicacion del algoritmo `Minimax` con `Poda Alfa-Beta` para crear un agente inteligente que tome las decisiones más optimas, utilizando el juego `Gato` tambien conocido como `Tres en linea` o `Tic-Tac-Toe`. El objetivo es explorar todas las jugadas posibles y elegir la mejor, asumiendo que el oponente también juega de manera perfecta.

## **Explicación del algoritmo utilizado**

### **Minimax**
El algoritmo Minimax es una forma de tomar decisiones en juegos de dos jugadores, especialmente en los que lo que gana uno, lo pierde el otro (juegos de suma cero). Este algoritmo básicamente crea un árbol de decisiones con todas las posibles jugadas desde la posición actual del juego. Los jugadores se turnan, y hay dos roles principales:

- **Maximizar (IA):** Este jugador busca obtener la mayor puntuación posible.
- **Minimizar (Jugador Humano):** Este jugador trata de hacer que la puntuación del oponente sea lo más baja posible.

Al final de cada camino en el árbol (es decir, cuando el juego termina), se asigna un valor dependiendo del resultado:

- Si la IA gana: **+10** puntos.
- Si el humano gana: **-10** puntos.
- Si hay empate: **0** puntos.

La idea es que el algoritmo empieza desde los resultados finales y calcula hacia atrás cuál sería la mejor jugada inicial. Así, el primer movimiento que se haga será el mejor posible, siempre y cuando el otro jugador también juegue de forma perfecta.

#### **Funcionamiento:**
1. El árbol de decisiones del juego se representa como un conjunto de estados (nodos) y movimientos posibles (ramas).
2. Los jugadores alternan turnos:
   - **Maximización:** Trata de maximizar la puntuación.
   - **Minimización:** Trata de minimizar la puntuación.
3. Se evalúan los valores de los nodos hoja utilizando una función de utilidad.
4. Se realiza un recorrido **de abajo hacia arriba** en el árbol:
   - Los nodos **Max** toman el valor máximo de sus hijos.
   - Los nodos **Min** toman el valor mínimo de sus hijos.

### **Poda Alfa-Beta**

La Poda Alfa-Beta es como una versión más rápida y eficiente del algoritmo Minimax. La idea es no perder tiempo analizando jugadas que, desde antes, ya sabemos que no van a cambiar el resultado final, en donde mientras se analiza el árbol de jugadas posibles, si se encuentra una rama que no puede mejorar el resultado para uno de los jugadores, se deja de analizar esa rama (esto es lo que se llama "poda"), y de esta manera, el algoritmo sigue funcionando igual que Minimax, pero se ahorra tiempo porque no evalúa movimientos innecesarios.

#### **Funcionamiento:**
1. Utiliza dos límites:
- **Alfa (α):** Es el mejor resultado que el jugador Max (la IA) puede conseguir hasta ahora.
- **Beta (β):** Es el mejor resultado que el jugador Min (el humano) puede asegurar hasta ahora.
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

## Análisis de Complejidad Temporal
La cantidad de trabajo que Minimax tiene que hacer depende de dos cosas:

1. **Factor de ramificación (b):** Es la cantidad de jugadas posibles en promedio en cada turno.
2. **Profundidad del árbol (d):** Es cuántos turnos hay desde el inicio hasta el final del juego.

Sin usar la Poda Alfa-Beta, Minimax revisa todas las posibles jugadas y eso se calcula como \(O(b^d)\). Esto significa que, mientras más opciones haya y más turnos se jueguen, el trabajo crece muy rápido. Por ejemplo, en el juego del Gato:

- Hay un máximo de 9 jugadas posibles en cada turno (\(b \leq 9\)).
- El juego puede durar hasta 9 turnos (\(d \leq 9\)).

En el peor caso, Minimax tendría que analizar \(9^9 \approx 387\) millones de jugadas.

Con **Poda Alfa-Beta**, el algoritmo no analiza opciones que no cambiarán el resultado, lo que reduce el trabajo. En el mejor caso, la complejidad baja a \(O(b^{d/2})\), o sea, explora menos de la mitad de las jugadas. 

### Minimax sin poda:
- **Complejidad:** \(O(b^d)\), donde:
  - \(b\): Número de movimientos posibles (factor de ramificación).
  - \(d\): Profundidad del árbol de decisiones.

Para **Tic-Tac-Toe**:
- \(b <= 9\), \(d <= 9\).
- Nodos a evaluar en el peor caso: \(9^9 = 387,420,489\).

### Minimax con poda alfa-beta:
- **Complejidad:** \(O(b^{d/2})\) en el mejor caso.
- Nodos a evaluar en el peor caso: \(9^{9/2} \approx 31,623\).

## Estructura del Código

- **Lenguaje de Programación:** C++
- **Compilador:** g++
- **Estructura del Código:**
Tablero: Clase que representa el estado del juego, verifica ganadores, jugadas válidas y otras operaciones sobre el tablero.
Sistema: Gestiona la lógica del juego, interactúa con Minimax + Alfa-Beta para decidir el mejor movimiento de la IA y mantiene el estado del turno actual.
App y main: Se encargan de la interfaz por consola y del menú, permitiendo al usuario interactuar con el programa. El jugador humano puede realizar su movimiento, mientras que la IA calculará el suyo usando Minimax con poda Alfa-Beta.

## Ejecución del Programa

Para compilar y ejecutar el programa, utiliza los siguientes comandos:

En la carpeta del proyecto, compila con:

g++ -o juego main.cpp App.cpp Sistema.cpp Tablero.cpp
Ejecuta:

./juego
Una vez iniciado, sigue las instrucciones en pantalla para jugar contra la IA.

