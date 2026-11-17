# Rigging, actuación y cuadro a cuadro

## Separar mecanismos y actuación

Un rig expone controles; el skinning determina cómo sigue la superficie a esos controles. Parenting a un hueso puede mover una pieza rígida; deformar piel requiere influencia distribuida. Drivers y constraints relacionan propiedades o movimientos. [Blender: Animation & Rigging y Skinning — S06](https://www.blender.org/features/animation/).

Diseñar controles a partir de las acciones del plano. FK sirve para dirigir cadenas y arcos; IK ayuda a sostener contactos. Probar cambios entre sistemas y espacios sin saltos. Los pesos automáticos son un comienzo: revisar hombros, cuello, mandíbula y zonas de contacto en las poses reales.

Las shape keys guardan posiciones correspondientes de los vértices. Crear formas sobre una topología estable y probar mezclas: sonrisa + boca abierta puede necesitar un correctivo aunque ambas funcionen por separado. No transferir formas entre mallas con índices diferentes sin establecer correspondencia. [Shape Keys — S07](https://docs.blender.org/manual/en/4.5/animation/shape_keys/introduction.html).

## Hacer que una acción tenga intención

Procedimiento propuesto: definir objetivo del personaje, poses principales y cambios de decisión; revisar la lectura en silueta; luego trabajar transiciones y acciones secundarias. Una captura de movimiento necesita retargeting, ajuste de proporciones y revisión de contactos. Una simulación de cola tampoco decide por sí sola dónde debe mirar el dinosaurio.

Para peso, evaluar apoyo, desplazamiento corporal, aceleración, frenado y recuperación. No imponer que el centro de masa esté siempre sobre un pie: una carrera incluye desequilibrio dinámico y fases aéreas. Evitar pies que patinan durante el apoyo y frenadas sin reacción. Mirar el plano a velocidad real: curvas suaves no garantizan una actuación clara.

Bibliografía artística: [Richard Williams, The Animator’s Survival Kit Animated — S08](https://www.bloomsbury.com/uk/discover/superpages/the-animators-survival-kit-animated/). La ficha editorial confirma su aplicación a animación tradicional, CGI y stop motion; estos criterios no son una transcripción de sus clases.

## «Cuadro a cuadro» puede significar tres trabajos

| Trabajo | Unidad de decisión |
|---|---|
| Animación dibujada | Qué dibujo mostrar y durante cuántos fotogramas. |
| Stop motion | Cuánto mover un objeto físico antes de fotografiarlo otra vez. |
| Análisis de cine / revisión VFX | Qué cambió entre fotogramas de un plano ya filmado. |

No confundirlos con «plano por plano», que trata la organización de tomas y montaje.

En animación, **timing** es la duración de la acción; **spacing**, la separación entre posiciones sucesivas. Mantener el mismo inicio y final permite cambiar sensación de velocidad mediante posiciones intermedias. Usar poses clave, breakdowns y después intermedios; onion skin permite comparar dibujos, pero hay que reproducir la secuencia para juzgar el ritmo. El manual de [OpenToonz — S09](https://opentoonz.readthedocs.io/en/latest/drawing_animation_levels.html) documenta dibujo, onion skin y rotoscopia.

Una X-sheet registra contenido por cuadro y capa. A 24 fps, exponer cada dibujo durante dos cuadros produce 12 dibujos por segundo si toda la secuencia mantiene ese patrón; el archivo sigue a 24 fps. Se pueden mezclar unos, doses y holds. No repetir todo el compuesto si solo el personaje requiere cadencia escalonada. [Xsheet/Timeline — S10](https://opentoonz.readthedocs.io/en/latest/working_in_xsheet.html).

## Stop motion: controlar la captura

Propuesta de preparación: fijar cámara, enfoque, exposición y balance de blancos cuando el efecto lo permita; evitar variaciones de luz ambiente; anotar posiciones y capturar una prueba de parpadeo. Revisar el fotograma capturado a resolución final, no solo el live view. Planear soportes y una toma limpia para retirarlos en composición.

El [manual de Dragonframe 3.7 — S11](https://www.dragonframe.com/download/Dragonframe%20User%20Guide%20-%20Mac.pdf) reúne herramientas de cinematografía, animación, timeline y X-sheet. Es una referencia histórica; comprobar el manual de la versión instalada para cámaras, drivers y controles actuales.

## Ejercicios propios

- Pelota: dos versiones con idénticos extremos y distinta separación de posiciones; comparar peso y velocidad.
- Personaje: giro de cabeza que anticipa un paso, con pie apoyado y mirada legible.
- Dibujo: acción de un segundo a 24 fps con exposiciones mixtas; entregar X-sheet y reproducción.
- Stop motion: secuencia corta con objeto rígido, sin variaciones accidentales de exposición.

Aceptar el movimiento cuando el objetivo y los contactos se entienden en reproducción, los controles no saltan y no hay deformaciones involuntarias. El criterio artístico puede requerir exageración deliberada.
