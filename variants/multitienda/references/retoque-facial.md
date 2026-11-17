# Rejuvenecimiento, limpieza de cutis y dientes digitales

Aplicar a fotografías o video según el pedido. Esta referencia trata modificación visual, no tratamientos de piel ni odontología clínica. Para editar una imagen raster mediante generación, respetar la herramienta/skill de imágenes aplicable; para video o escenas 3D, usar el flujo de tracking y composición correspondiente.

Las recetas siguientes son una síntesis de producción propuesta. Los manuales documentan herramientas; los papers demuestran métodos de investigación en sus condiciones. Su existencia no demuestra disponibilidad de modelos, licencias o rendimiento local.

## Elegir el alcance del retoque

Inspeccionar resolución de la cara, movimiento, oclusiones y referencias. Si el usuario no pidió cambiar identidad, preservar rasgos, asimetrías y actuación. No interpretar «limpiar cutis» como cambiar forma facial o borrar todos los poros. Para edad, usar una referencia estética o fotos aportadas cuando existan; una edad numérica no define por sí sola un resultado visual exacto.

| Pedido | Primera opción a evaluar | Cuándo escalar |
|---|---|---|
| Grano, mancha o brillo localizado | Máscara seguida + corrección/paint | Deformación, oclusiones o cambios fuertes de luz. |
| Uniformar tono y suavizar cutis | Corrección por regiones y escala de detalle | Si afecta contornos, textura o coherencia temporal. |
| Atenuar ojeras o arrugas | Corrección de contraste local y textura | Cambios volumétricos requieren warp o 3D. |
| Rejuvenecer/envejecer | Tratamiento de apariencia con referencia | Silueta, volumen o transformación fuerte: geometría y trabajo adicional. |
| Blanquear dientes existentes | Máscara dental y ajuste moderado | No genera una pieza ausente ni corrige geometría. |
| Agregar diente faltante | Parche/proyección para vista limitada | Habla, perfil, paralaje y oclusiones complejas: diente/arcada 3D. |

## Base temporal compartida

Separar movimiento de cabeza, deformación de piel y movimiento mandibular. Elegir cuadro de referencia con buena visibilidad y dividir el plano cuando el área se oculte o cambie demasiado. Una homografía puede servir a una región aproximadamente plana; no describe toda una cara expresiva.

PowerMesh sigue superficies no planas y permite unwarp, retoque y rewarp. Ese proceso puede perder información y estirar píxeles cuando una zona desaparece, como al cerrar el ojo. No tratarlo como transformación reversible perfecta. [Mocha, secciones PowerMesh y Unwarping — S31](https://borisfx.com/documentation/mocha/12.5.2/).

Otra opción es producir vectores, corregir un cuadro y propagar con VectorDistort. [Nuke Smart Vector Toolset — S32](https://learn.foundry.com/nuke/13.0/content/comp_environment/smartpaint/smartvector.html). En ambos casos, comprobar pérdidas de seguimiento y nuevas superficies; no extender indefinidamente un único parche ni regenerar cada cuadro de manera independiente sin control temporal.

## Limpieza de piel conservando textura

1. Delimitar piel y excluir ojos, cejas, pestañas, pelo, labios y objetos que pasan por delante. Revisar la máscara en movimiento.
2. Separar problemas de tono amplio de detalles puntuales. Corregir el color o contraste de la zona antes de borrar estructura que podría ser una sombra real.
3. Para imperfecciones concretas, tomar material de una región/cuadro compatible y propagarlo con el movimiento. Clone y Reveal son operaciones distintas documentadas por [RotoPaint — S33](https://learn.foundry.com/nuke/current/content/comp_environment/rotopaint/drawing_paint_strokes.html).
4. Usar suavizado selectivo por escala e intensidad; comparar poros y contraste con zonas vecinas. Revisar también a resolución final, donde un exceso de detalle puede distraer.
5. Reintegrar sin bordes evidentes ni cambios de grano; comparar antes/después y diferencia para encontrar zonas modificadas accidentalmente.

El manual de [BCC+ Beauty Studio — S29](https://borisfx.com/documentation/continuum/bcc-plus-beauty-studio/) documenta aislamiento de piel y suavizado por detalle. La guía de [Resolve 18, p. 106 — S30](https://documents.blackmagicdesign.com/UserManuals/DaVinci-Resolve-18-Colorist-Guide.pdf) muestra Face Refinement, análisis y máscara que sigue la cara. Son alternativas si están disponibles; no asumir que plugins comerciales o funciones Studio ya están instalados.

No fijar un radio universal en píxeles: depende de la resolución y del tamaño facial en cuadro. Si se usa separación de frecuencias, comprobar que reconstruir las bandas sin cambios reproduce la entrada; halos y cambios de rango indican una composición incorrecta.

## Rejuvenecimiento y envejecimiento

Distinguir textura, tono, volumen aparente y silueta. Atenuar líneas no equivale a reconstruir una cara de otra edad. Comparar referencias con luz y expresión similares para no confundir sombra con envejecimiento. Mantener pliegues de actuación: borrar el surco de una sonrisa puede quitar vida incluso si conserva la semejanza en reposo.

Diseño propuesto: comenzar con cambios locales moderados; comparar neutro, sonrisa, boca abierta, parpadeo y perfil. Escalar a deformación o 3D solo cuando lo pida el objetivo. Cuello, manos, pelo o vestuario pueden contradecir la edad buscada: señalarlo y ajustar el alcance con el usuario, sin ampliarlo automáticamente.

[FRAN, Disney Research — S34](https://studios.disneyresearch.com/2022/11/30/production-ready-face-re-aging-for-visual-effects/) aborda re-aging con una red entrenada sobre datos sintéticos, identidad, estabilidad y controles locales. Tomarlo como referencia de investigación; el título «production-ready» no garantiza resultados en este metraje ni que exista una implementación oficial descargable. Verificar cualquier implementación y sus permisos antes de adoptarla. No prometer un número exacto de años ni intercambiar cara por la de otra persona como solución implícita.

## Reponer dientes faltantes

Primero identificar **qué pieza o espacio debe cambiar, en qué arcada y durante qué cuadros**. Si el video no lo revela y afecta el resultado, pedir aclaración. Distinguir referencias observadas de geometría inventada. Una fotografía parcial no permite conocer con certeza la forma real de un diente ausente.

Para una vista casi frontal y corta, evaluar parche con seguimiento, ajuste de perspectiva y máscaras. Usar diente vecino como referencia de tamaño/color puede ayudar, pero duplicarlo literalmente puede producir anatomía o asimetrías extrañas. En giros y habla, preparar geometría simplificada ajustada al arco dental y evaluar desde la cámara.

**Anclaje:** dientes superiores con maxilar/cabeza; inferiores con mandíbula. No ligar toda la dentadura al mismo controlador ni deformar dientes rígidos como piel. La mandíbula puede combinar rotación y traslación; ajustar a la actuación observada en lugar de asumir una bisagra perfecta. Verificar contacto aparente y espacios entre piezas.

**Visibilidad:** labios, lengua, encías, piezas existentes y manos pueden ocultar el añadido. Los labios no son una ventana rígida; revisar apertura, cierre y fonemas. Cuando el labio cubre una pieza, debe desaparecer gradualmente con el borde y blur correspondientes, sin sobresalir ni perforarlo.

**Apariencia:** igualar valor y matiz de los dientes vecinos, variación de superficie, reflejos, sombra de la cavidad y espesor visible. Evitar blanco puro uniforme. Si el plano necesita un modelo de esmalte más complejo, verificar referencias de material; no declarar que un shader genérico representa toda su óptica.

El trabajo [Model-Based Teeth Reconstruction — S35](https://studios.disneyresearch.com/2016/11/11/model-based-teeth-reconstruction/) estudia inferencia de una fila dental personalizada usando pocas fotografías y un modelo previo. Es evidencia de un enfoque de reconstrucción, no una solución automática aquí instalada ni una fuente para afirmar forma verdadera de una pieza faltante. El procedimiento de sustitución anterior es una adaptación de producción.

## Otros efectos afines

Maquillaje digital, atenuación de cicatrices, recoloración de labios, cambios de cejas y colmillos pueden reutilizar máscaras, tracking, texturas o geometría. Elegir según cambie solo apariencia o también silueta/oclusión. Modificar únicamente el rasgo pedido; conservar una versión original y controles de intensidad cuando sea viable.

## Prueba de aceptación propuesta

Revisar al menos los eventos relevantes del plano: giro, expresión máxima, apertura/cierre, entrada de mano y reaparición después de oclusión. Comparar a velocidad real y cuadro a cuadro:

- Identidad y expresión reconocibles, excepto cambios estilizados pedidos.
- Textura de piel estable; sin parche inmóvil, halos, suavizado plástico ni color que bombea.
- Dientes con cantidad, forma y posición consistentes; sin deformación gelatinosa.
- Superior/inferior siguen sus movimientos; labios y lengua tapan correctamente.
- Luz, enfoque, motion blur y grano compatibles en cada región.

Entregar antes/después, tramo de reproducción y máscaras o escena editable según el programa. Declarar cualquier cuadro aún problemático; una imagen fija correcta no valida el video.
