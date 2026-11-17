# Automatización por agente

## Qué automatizar y qué evaluar visualmente

Un agente puede construir escenas, materiales y controles, distribuir objetos, configurar cámaras, animar parámetros, preparar cachés y lanzar renders mediante interfaces disponibles. Eso no demuestra anatomía, actuación ni integración correctas. Esas cualidades necesitan referencias y revisión de imágenes/secuencias.

Descubrir primero programas, versiones y recursos existentes. No imponer Blender si el proyecto ya está en otra aplicación. La investigación verificó Blender **4.5.15 LTS** en `/home/leandro/Escritorio/Aplicaciones/blender-4.5.15-linux-x64/blender`; es contexto local de esta entrega, no una dependencia portable ni una garantía para futuras sesiones.

## Scripts reproducibles

La [API oficial de Blender 4.5 — S28](https://docs.blender.org/api/4.5/) distingue datos, contexto y operadores. Consultar la API concreta y comprobar disponibilidad antes de fijar nombres de sockets o propiedades. Preferir acceso directo a datos cuando evita depender de selección/modo/UI; algunos operadores requieren contexto válido.

Convenciones propuestas para un trabajo real:

- Separar configuración de lógica: rutas, unidades, fps, cuadros, resolución, motor y salida.
- Usar nombres de objetos y colecciones identificables; una segunda ejecución no debería duplicar toda la escena accidentalmente.
- Guardar una nueva versión antes de operaciones que cambien topología o datos existentes.
- Registrar versión, dispositivo efectivo y parámetros; no afirmar uso de GPU porque solo se seleccionó una preferencia.
- Guardar archivos y dependencias en ubicaciones explícitas. No lanzar toda la secuencia antes de validar una muestra representativa.

La validación debe ser proporcional: existencia de archivos, duración/fps/rango, recursos sin perder y ausencia de errores, junto con inspección visual. No hace falta crear infraestructura de tests para mover una luz. Para un script repetible que transforma cámaras o coordenadas, sí conviene una prueba de proyección conocida.

## Contrato mínimo de un plano

Registrar en el formato que ya use el proyecto:

| Dato | Ejemplo ilustrativo |
|---|---|
| Plano y versión | living_010 / v003 |
| Material original | Ruta y metadatos verificados |
| Tiempo | Cuadros inicial/final, fps y offset hacia el original |
| Espacio | Unidades, escala, convención de ejes y cámara |
| Color | Entrada, trabajo, vista, salida y configuración |
| Dependencias | Texturas, modelos, tracking, cachés, fuentes/licencias |
| Revisión | Cuadros y tramo inspeccionados, defectos pendientes |

Son ejemplos de campos, no valores que deban inventarse. Si el video usa tiempos variables, preservar sus timestamps o conformar conscientemente antes de trabajar por índice de cuadro; comprobar sincronización.

## Cuándo cambiar de método

Si una solución no mantiene registro con el metraje, mejorar o reemplazar tracking antes de detallar. Si la geometría no permite la deformación, corregirla antes de aumentar resolución. Si falla una API, inspeccionar error y versión antes de reintentar. La habilidad consiste en detectar el límite observado y escoger el siguiente experimento útil.

Un informe final debe distinguir: código escrito, ejecución realizada, render producido e inspección visual realizada. Esas cuatro cosas no son intercambiables. Esta skill contiene procedimientos y fuentes; no instala aplicaciones, modelos de IA ni licencias comerciales.
