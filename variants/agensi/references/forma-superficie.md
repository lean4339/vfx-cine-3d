# Escultura, modelado y materiales

Usar para construir o corregir una forma. Los criterios de trabajo y ejercicios siguientes son una síntesis práctica propia; el alcance de consulta de cada fuente está en [fuentes.md](fuentes.md).

## Escultura: mirar masas antes que poros

Organizar referencias frontal, perfil y tres cuartos; separar perspectiva de proporción. Definir silueta, masas principales, planos y relación entre volúmenes antes de detalles. En una cabeza, comparar cráneo, mandíbula, órbitas y proyección del hocico o nariz; en un cuerpo, relación entre caja torácica, pelvis y extremidades. No extrapolar anatomía humana a un dinosaurio: buscar referencias específicas del animal o de la criatura diseñada.

Comprobar la forma con material neutro, iluminación lateral y varias vistas. Una escama convincente no corrige una mandíbula mal colocada. La bibliografía tradicional de [Lucchesi y Malmstrom — S01](https://www.brunolucchesi.com/books) complementa el estudio artístico; su ficha no documenta una receta digital.

En Blender, elegir resolución adaptativa y pinceles según la operación. El [manual de escultura — S02](https://docs.blender.org/manual/en/4.5/sculpt_paint/sculpting/introduction/index.html) organiza pinceles, máscaras, Face Sets y Multiresolution. Antes de cambiar resolución, conservar una versión y decidir qué datos deben sobrevivir.

## Topología: diseñar para el uso

Esculpir y preparar para animación son tareas relacionadas, pero una malla uniforme no garantiza buenos pliegues. El manual distingue remeshing automático de retopología orientada a deformación. Un remesh puede ser útil durante la construcción; revisar el flujo de caras para mandíbula, párpados y articulaciones. No convertir «todo debe ser quads» en una regla universal: la deformación, la subdivisión y el destino mandan. [Remeshing / Retopology — S03](https://docs.blender.org/manual/en/4.5/modeling/meshes/retopology.html).

Prueba propuesta: abrir mandíbula, cerrar párpados y llevar cuello/extremidades a los extremos del plano. Observar pérdida de volumen, intersecciones y pinzamientos. Si falla, revisar topología, pesos y correctivos antes de añadir subdivisiones. La topología contribuye al resultado junto con el rig y el skinning.

El detalle necesario depende de tamaño en pantalla, silueta, movimiento, iluminación y distancia. Decidirlo desde la cámara final; una cara de pocos píxeles no necesita el mismo trabajo que un primerísimo primer plano.

## UV y texturas

Las UV relacionan superficie e imagen. Revisar estiramiento con una cuadrícula, continuidad de costuras y densidad de texeles. Concentrar resolución donde el plano la necesita; prever margen alrededor de islas para filtrado. Los materiales procedurales pueden usar otras coordenadas y no requieren siempre UV. [UV Editor — S04](https://docs.blender.org/manual/en/4.5/editors/uv/introduction.html).

## Decidir qué hace cada mapa

| Control | Decisión observable |
|---|---|
| Color base | Variación de pigmentación; evitar hornear reflejos y sombras accidentales en un material que se volverá a iluminar. |
| Rugosidad | Anchura y definición de reflejos; no equivale a aclarar u oscurecer el color. |
| Normal / bump | Cambian la orientación usada en sombreado; no producen por sí solos una silueta nueva. |
| Displacement | Desplaza geometría según el método del motor; requiere resolución y límites adecuados. |
| Subsurface scattering | Dispersión bajo la superficie: ajustar con escala de escena y espesor. |
| Transmisión / IOR | Paso y refracción de luz; no confundir con alpha ni con dispersión subsuperficial. |

El modelo de capas y sus parámetros se documentan en [Principled BSDF — S05](https://docs.blender.org/manual/sr/4.5/render/shader_nodes/shader/principled.html). La distinción matemática entre reflexión, transmisión y volúmenes se estudia en los capítulos 9 y 11 de [PBRT — S21](https://pbr-book.org/4ed/contents).

Interpretar mapas de color con su espacio declarado y mapas numéricos como datos cuando corresponde. Un mapa normal tratado como color altera las normales. [Color Management — S24](https://docs.blender.org/manual/fi/4.5/render/color_management.html).

## Ejercicio y criterio de salida

Propuesta: construir una cabeza sencilla con mandíbula móvil; producir vista neutra, wireframe, cuadrícula UV y poses extremas. Después comparar tres rugosidades bajo la misma luz. Entregar una forma legible y deformable, con texturas estables. No considerar terminado un personaje solo porque se ve bien en la pose de reposo.
