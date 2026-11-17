# Casos de producción

Los siguientes son diseños de trabajo propios, todavía no ejecutados sobre un metraje. Elegir duración y parámetros al inspeccionar el material real.

## Dinosaurio entrando al living

**Problema dominante:** relación con el espacio y peso. Abrir [cine/cámara/luz](cine-camara-luz.md), [movimiento](movimiento.md) y [render/composición](render-composicion.md).

Primero determinar si la cámara está fija o en movimiento. Definir suelo, puerta, muebles y una medida de referencia. Probar un volumen simple entrando, pasando detrás de un mueble y apoyando una pata. Esta prueba debe revelar si perspectiva, escala, oclusión y sombras funcionan antes de invertir en escamas.

Elegir o construir el dinosaurio según el plano. Un modelo existente puede ahorrar trabajo si su calidad, deformación y licencia sirven. Para anatomía, no convertir una caminata humana capturada en cuadrúpedo sin adaptación. Diseñar poses, apoyos y ritmo; añadir cola y tejido secundario después de resolver locomoción.

Modelar receptores y obstáculos necesarios para sombras/reflejos, incluidos los que no se vean directamente. Si una persona pasa por delante, separar su silueta del plate con máscaras adecuadas. Los identificadores del render no resuelven esa persona real. Las referencias técnicas de pases están en [Blender — S23](https://docs.blender.org/manual/en/4.5/render/layers/passes.html).

**Aceptar cuando:** no hay deriva, el apoyo no resbala, la acción tiene peso, la oclusión es correcta y luz/enfoque/grano son compatibles. **Entregar:** escena editable, recursos referenciados, tramo de revisión y compuesto.

## Transformacion facial estilizada

**Problema dominante:** preservar actuación y continuidad de una cara deformable. Abrir [forma/superficie](forma-superficie.md), [movimiento](movimiento.md) y [retoque facial](retoque-facial.md).

Dividir el efecto en pose rígida de cabeza, expresión y apariencia. Un cambio verde leve podría resolverse con máscara y color; una mandíbula exagerada o nueva silueta puede requerir geometría y correctivos. Inspeccionar boca abierta, parpadeo, giro de perfil, pelo y manos sobre la cara antes de elegir método.

MediaPipe puede entregar landmarks, coeficientes de expresión y matriz de transformación. Son estimaciones para conducir un efecto, no una identidad 3D escaneada. Comprobar coordenadas, espejo izquierda/derecha, escala y correspondencia temporal; el manual advierte que los nombres left/right corresponden al sujeto. [Face Landmarker — S27](https://developers.google.com/edge/mediapipe/solutions/vision/face_landmarker).

Adaptar una superficie a sus rasgos. Conservar ojos, boca y expresión donde convenga; resolver zonas nuevas si la deformación descubre píxeles inexistentes. La topología final necesita controles para cerrar párpados y labios sin intersecciones. Ajustar luz y sombras con el video, no solo con una vista frontal neutra.

**Aceptar cuando:** sigue siendo reconocible, habla/parpadea sin deslizamiento, hay continuidad en perfiles y oclusiones, y el borde de máscara se integra. **Límite:** sin metraje y referencias no prometer calidad de largometraje ni automatización completa.

## Retoque de piel y diente faltante en un mismo plano

Separar tareas para poder comparar cada intervención. En piel, comenzar por una corrección localizada y estable. En boca, identificar arcada y movimiento; dientes superiores siguen el maxilar/cabeza e inferiores la mandíbula. Un simple parche podría servir en una sonrisa casi fija; un giro y habla prolongada pueden exigir 3D.

Trabajar con el [procedimiento facial](retoque-facial.md). Usar un tramo que incluya máxima apertura, cierre y una oclusión. La prueba pasa si el diente mantiene forma y anclaje, desaparece detrás del labio y responde a la luz de la cavidad, mientras la piel conserva detalle y expresión. No dar por resuelta la secuencia por un único retrato retocado.
