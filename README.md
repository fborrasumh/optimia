# OptimIA

Laboratorio inteligente de Investigación Operativa. Aplicación web de un solo fichero.

**Usar la app:** https://fborrasumh.github.io/optimia/

**Idiomas:** español (por defecto), inglés, portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

OptimIA ayuda al estudiantado de Investigación Operativa (asignatura 2790, Grado en Ingeniería Informática en Tecnologías de la Información) a recorrer el ciclo **comprender → modelizar → resolver → interpretar → detectar errores → volver a practicar**. Evalúa cómo se llega a la solución, no solo la solución.

- **11 tipos de problema en 4 unidades**, generados con semilla (la misma semilla da siempre el mismo problema):
  - U1: producción (máx.) y requisitos mínimos (mín.) con 2 variables y método gráfico.
  - U2: producción con 3 productos (Simplex, dualidad) y mezcla con =, ≥ y ≤ (Simplex en dos fases).
  - U3: producción entera (Branch & Bound) y selección de proyectos con variables binarias y restricciones lógicas.
  - U4: camino mínimo, árbol de expansión mínima, flujo máximo, transporte y asignación.
- **Modelización paso a paso:** variables (significado), función objetivo, restricciones y dominio; o la red / la tabla en U4. El código compara cada parte con el modelo correcto, reconoce formas equivalentes (filas escaladas, ≥ reescritas como ≤) y clasifica los errores **E01–E15**.
- **Diagnóstico por recálculo:** si la solución del estudiante es la óptima de *su* modelo erróneo, lo dice; detecta solución factible no óptima, máximo/mínimo confundidos, redondeo de la relajación, violación de capacidades o de conservación del flujo.
- **Algoritmos visibles paso a paso** sobre el modelo del estudiante y sobre el correcto: región factible con restricciones activables y recta de nivel desplazable, tableaux del Simplex (fase 1 y 2) con la explicación de cada pivote, árbol de Branch & Bound, Dijkstra, Kruskal, Prim, Edmonds-Karp (con corte mínimo), esquina noroeste + MODI y método húngaro.
- **Nota orientativa** con la ponderación Modelización 2 · Resolución 4 · Cálculos 2 · Interpretación 2 (configurable).
- **Dominio multidimensional** (conceptos, modelización, cálculo, algoritmo, interpretación) por unidad y objetivos O1–O5; **repetición espaciada** de cada error a 1, 3, 7 y 21 días; **sesión diaria** de 20 minutos calculada automáticamente.
- **Modos** entrenamiento (comprobar y pistas), desafío (pistas a demanda) y examen (sin ayudas); **simulacro de examen** por bloques U1–U3 y U4.
- **Laboratorio** que sustituye a RStudio: lector de modelos en texto (`max 3x1 + 2x2`, `x1 + x2 <= 4`, `int x1`, `bin x2`) con Simplex, sensibilidad (precios sombra, rangos) y B&B; editor de redes con Dijkstra, Floyd-Warshall, Kruskal, Prim y flujo máximo; tablas de transporte y asignación.
- **Tutora socrática de IA opcional.**
- Exportación e importación del progreso en JSON.

## Cómo se usa la IA

**La IA nunca es el solver.** Todos los cálculos los hacen algoritmos deterministas en JavaScript dentro del navegador, contrastados con oráculos independientes (enumeración de vértices, fuerza bruta entera, Bellman-Ford, corte mínimo por enumeración, Simplex general para transporte, permutaciones para asignación) en miles de casos aleatorios (`node tests/solvers_test.js`).

La IA, opcional, solo hace de **tutora socrática** con la clave de cada persona (OpenAI, Google Gemini o Anthropic Claude; la clave se guarda solo en el navegador). Recibe el enunciado, el modelo del estudiante y el diagnóstico calculado por el código, **nunca la solución**; además, el código elimina de su respuesta cualquier frase que contenga cifras del óptimo que no estén en el enunciado o que escriba una restricción correcta que el estudiante tiene mal. No está disponible en modo examen hasta entregar.

## Privacidad

No hay cuentas ni servidor. Modelos, respuestas, progreso y clave se guardan en el navegador (IndexedDB y localStorage). Solo sale información si se escribe a la tutora: el texto se enmascara (correos, teléfonos…) y antes del primer envío de la sesión se muestra lo que sale.

## Límites

- La nota es **orientativa** para practicar y no sustituye a la evaluación de la asignatura.
- El catálogo es de 11 plantillas; el profesorado aún no puede crear plantillas ni exámenes propios (prevista una versión docente).
- La tutora de IA puede equivocarse; el filtro de fugas es una protección, no una garantía absoluta.
- El laboratorio admite hasta 8 variables y 10 restricciones; los nodos de la red no se arrastran con el ratón.
- No es una PWA instalable: es un único HTML que funciona sin conexión una vez abierto (la tutora necesita red).
- Probada con IA simulada (OpenAI), no con una clave real.

## Autoría

Fernando Borrás Rocher y Laura Antón Sánchez (Universidad Miguel Hernández de Elche).

### Origen de la idea

A partir de la idea y la especificación IO-TRAINER de la profesora Laura Antón Sánchez para la asignatura Investigación Operativa (2790) del Grado en Ingeniería Informática en Tecnologías de la Información.

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · Laura Antón Sánchez [0000-0003-4707-8844](https://orcid.org/0000-0003-4707-8844)

## Cómo citar

Borrás Rocher, F. y Antón Sánchez, L. (2026). *OptimIA* (v1.0.0) [Software]. (DOI en trámite)

## Licencia

MIT. Véase [LICENSE](LICENSE).
