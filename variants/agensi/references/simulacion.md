# Simulación física dirigida

Elegir el fenómeno y la representación antes de subir resolución. La física aproxima comportamientos; el plano determina qué detalles importan. No simular ropa, saliva o destrucción si no contribuyen al pedido.

| Fenómeno | Representación habitual | Riesgo visible |
|---|---|---|
| Objetos y fragmentos rígidos | Transformaciones, colisiones y restricciones | Interpenetración, vibración, rebotes impropios. |
| Tela, pelo y cuerpos blandos | Puntos, superficies y restricciones | Estiramiento, penetraciones, pérdida de forma. |
| Humo y fuego | Campos volumétricos de densidad, temperatura y velocidad | Escala equivocada, volumen recortado o movimiento uniforme. |
| Agua | Métodos de superficie y/o partículas con malla de cálculo | Pérdida de volumen, superficie que parpadea. |

La tabla es una clasificación de trabajo, no un único algoritmo para cada fenómeno. [Vellum — S13](https://www.sidefx.com/docs/houdini/vellum/index.html) documenta un enfoque de dinámica basada en posiciones para varios materiales. [Pyro — S14](https://www.sidefx.com/docs/houdini/pyro/intro.html) documenta humo/fuego volumétrico y lo diferencia de FLIP; Pyro no es la elección general para una superficie de agua.

## Orden de diagnóstico propuesto

1. Comprobar escala, tiempo, geometría de colisión, orientación y transformaciones.
2. Confirmar que fuentes, fuerzas y restricciones producen el movimiento básico.
3. Revisar subpasos y convergencia del solver; después aumentar resolución espacial si falta detalle.
4. Inspeccionar el tramo difícil y realizar caché con parámetros identificables.
5. Repetir la simulación cuando cambien geometría, tiempos o parámetros que invaliden el caché.

Subpasos y resolución resuelven problemas diferentes: más detalle espacial no corrige necesariamente una colisión que se saltea entre instantes. La documentación de Vellum enlaza tratamientos separados de colisiones, masa/espesor y telas de distinta resolución. Para fundamento matemático, estudiar advección, presión, pasos de tiempo y partículas en el índice de [Bridson — S12](https://www.routledge.com/Fluid-Simulation-for-Computer-Graphics-Second-Edition/Bridson/p/book/9781315266008); no atribuirle valores universales de producción.

## Costo, cachés y dirección artística

Reducir a la mitad el tamaño de celda de una **grilla densa tridimensional con el mismo dominio** multiplica por ocho la cantidad de celdas. Es una deducción geométrica, no una predicción exacta de tiempo: estructuras dispersas, solver y pasos temporales cambian el costo real.

Probar a baja resolución para decidir ritmo y trayectoria. Una tela puede simularse con una malla menor y transferirse a una superficie detallada, si el método conserva las deformaciones necesarias. En humo, distinguir el movimiento de densidad del sombreado que lo hace visible: cambiar el material no resuelve una emisión equivocada.

Registrar rango de cuadros, fps, semilla cuando exista, geometría, versión y ubicación de caché. Conservar suficiente preroll si el fenómeno necesita asentarse. Evaluar una secuencia, no un único cuadro favorable.

Ejercicio propio: una cortina que el dinosaurio desplaza al pasar. Primero animar el collider, después lograr contacto y caída; agregar detalle solo cuando no hay penetraciones relevantes. El resultado se acepta por continuidad, interacción y lectura del plano, no porque el solver haya terminado sin error.
