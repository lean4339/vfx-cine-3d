# Cine, fotografía, cámara e iluminación

## Encuadre y relato

Antes de colocar una luz, decidir dónde debe mirar el espectador, qué revela el plano y cómo continúa la acción. Separar **composición de encuadre** (organización visual) de **composición digital** (integración de imágenes). El índice de [The Visual Story — S17](https://shop.elsevier.com/books/the-visual-story/block/978-0-08-055169-2) ofrece espacio, línea, forma, tono, color, movimiento y ritmo como ámbitos de estudio.

Propuesta de análisis: revisar tamaño del sujeto, espacio negativo, líneas dominantes, separación de valores, entradas/salidas, dirección de mirada y continuidad entre cortes. No imponer tercios ni simetría como reglas universales. Un dinosaurio puede resultar más amenazante parcialmente oculto si esa es la intención narrativa.

Para desglosar una secuencia, registrar plano, duración, acción, encuadre, movimiento de cámara y punto de corte. [Film Directing: Shot by Shot — S18](https://mwp.mwp.com/catalogs/MWP_Cat2015.pdf) es bibliografía de dirección y visualización; no sustituye los manuales de animación cuadro a cuadro.

## Leer la cámara real

Anotar resolución, relación de aspecto, fps, exposición, lente/sensor si se conocen, enfoque, estabilización y posibles recortes. No deducir una focal exacta solo por su «aspecto cinematográfico». Posición de cámara y campo de visión deben resolverse conjuntamente; cambiar focal desde una posición fija cambia el encuadre, mientras cambiar posición altera las relaciones de perspectiva.

El [American Cinematographer Manual — S15](https://theasc.com/news/announcing-new-edition-of-american-cinematographer-manual/) reúne secciones específicas de lentes, profundidad de campo, medición y formatos. Se verificó su índice; para cifras técnicas consultar el capítulo correspondiente.

Para un modelo pinhole, `p ~ K [R|t] P`: K representa intrínsecos y R/t transformación entre mundo y cámara. La distorsión se trata adicionalmente. Al redimensionar el metraje hay que ajustar los intrínsecos en píxeles. [OpenCV calib3d — S19](https://docs.opencv.org/4.13.0/d9/d0c/group__calib3d.html).

## Matchmoving

Elegir puntos del entorno rígido, distribuidos espacialmente y con continuidad. Excluir personas, reflejos y objetos independientes al resolver la cámara. Reconstruir cámara, establecer suelo/orientación y asignar escala con una medida fiable; una reconstrucción monocular no entrega automáticamente metros reales.

Poca traslación o paralaje dificulta recuperar profundidad. Un paneo puro puede requerir un método específico o trabajo 2.5D. No aceptar una solución solo por un error promedio bajo: revisar evolución por cuadro y colocar geometría de prueba sobre el suelo. [Solve y Graph View — S20](https://docs.blender.org/manual/fr/4.5/movie_clip/tracking/clip/toolbar/solve.html).

Definir un flujo de lente coherente: trabajar sobre metraje sin distorsión y redistorsionar los elementos al volver al original, o realizar una composición completa que restituya la distorsión una sola vez. Mantener overscan cuando sea necesario. Rolling shutter, estabilización y cambios de zoom pueden exigir tratamiento adicional; no asumir que un solver rígido los absorbe.

## Reconstruir la iluminación

Identificar dirección, tamaño aparente de fuentes, intensidad relativa, temperatura/tinte, rebotes y obstáculos. La suavidad de sombras depende del tamaño angular de la fuente desde el sujeto; bajar potencia no convierte una luz dura en blanda. Key, fill y separación describen funciones, no la obligación de usar tres lámparas. [ARRI Lighting Handbook, secciones 1–2 — S16](https://www.arri.com/resource/blob/83996/409091c612f371b0c68b41d9dcb636db/arri-lighting-handbook-english-data.pdf).

Propuesta: comenzar con una esfera gris, una superficie reflectante y geometría de contacto. Ajustar dirección y dureza antes de textura. Un HDRI aporta ambiente, pero fuentes cercanas pueden necesitar luces y geometría locales para sombras/paralaje coherentes. Modelar superficies fuera de cuadro cuando sus reflejos o sombras importen.

Para el dinosaurio, revisar contacto de patas, sombra sobre muebles y reflejos del piso. Para la cara, comparar sombra de nariz, brillos y transición hacia cuello. No inventar negros intensos por «AO» si el living tiene rebotes claros.

## Comprobación propuesta

Capturar un cuadro inicial, uno con mayor giro y otro con oclusión. Superponer referencias de cámara y comparar un objeto gris antes del personaje final. La prueba pasa cuando los puntos no derivan, el suelo sostiene la geometría y luz/enfoque son compatibles con el metraje; una vista aislada atractiva no es suficiente.
