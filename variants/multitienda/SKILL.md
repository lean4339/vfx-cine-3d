---
name: vfx-cine-3d
description: Investigar, construir y revisar VFX sobre video y escenas 3D con fuentes técnicas. Aplicar a escultura, materiales, rigging, animación cuadro a cuadro, stop motion, simulación, cámara, iluminación, render y composición; también rejuvenecimiento facial, limpieza de cutis, retoque de piel y reemplazo digital de dientes faltantes. Incluye tracking y preservación de expresión; no trata procedimientos médicos ni sustituye la generación de imágenes sueltas.
---

# VFX, cine y animación 3D

Resolver el plano según sus pistas visuales: forma, actuación, perspectiva, contacto, luz y respuesta de cámara. Trabajar en español salvo preferencia distinta. Explicar los términos al introducirlos y vincular cada decisión con lo que cambia en pantalla.

## Elegir el trabajo necesario

Identificar si el pedido es investigación, enseñanza, planificación, ejecución o diagnóstico. Una consulta bibliográfica no autoriza producir una película; un pedido de ejecución no se satisface solo con un plan.

Inspeccionar los archivos disponibles antes de pedir información. Para ejecutar, establecer metraje, rango de cuadros, fps, resolución, color de entrada/salida, efecto, programa y versión. Si todavía no hay metraje, avanzar con un diseño explícitamente provisional; no inventar cámara, tracking, rendimiento ni pruebas visuales.

Elegir entre corrección 2D, proyección 2.5D, objeto rígido, personaje deformable o simulación según el plano. No construir un humano completo para cambiar únicamente una cara. No resolver cámara 3D cuando una cámara fija calibrada basta. No confundir apariencia estilizada con un fallo que haya que eliminar.

## Consultar solo las referencias pertinentes

| Trabajo | Referencia |
|---|---|
| Escultura, anatomía, silueta, topología, UV y materiales | [Forma y superficie](references/forma-superficie.md) |
| Rigging, actuación, peso, mocap, animación 2D y stop motion | [Movimiento y cuadro a cuadro](references/movimiento.md) |
| Humo, fuego, agua, ropa, pelo y destrucción | [Simulación](references/simulacion.md) |
| Encuadre, fotografía, continuidad, cámara y luz | [Cine, cámara e iluminación](references/cine-camara-luz.md) |
| Path tracing, GPU, pases, color, alpha, rotoscopia y acabado | [Render y composición](references/render-composicion.md) |
| Scripts, reproducibilidad y evaluación visual | [Automatización](references/automatizacion.md) |
| Rejuvenecer/envejecer, limpiar cutis, corregir manchas, ojeras y dientes faltantes | [Retoque facial y dental](references/retoque-facial.md) |
| Dinosaurio en el living o Transformacion facial estilizada | [Casos aplicados](references/casos.md) |
| Manuales, libros, capítulos y estado de consulta | [Bibliografía comentada](references/fuentes.md) |

## Método de producción

1. Formular qué debe percibir el espectador y qué evidencias demostrarán que funciona. Distinguir restricción del metraje y elección artística.
2. Probar primero la incertidumbre dominante: superposición de tracking, volumen sencillo iluminado, poses o máscara. Elegir un tramo que contenga el giro, contacto u oclusión difícil.
3. Refinar únicamente lo que necesita ese plano. Comprobar silueta y deformación antes del detalle; contacto y luz antes de aumentar muestras.
4. Guardar una escena editable y producir una vista previa. Evaluar cuadros críticos y reproducción a velocidad real. Un comando exitoso no demuestra credibilidad visual.
5. Corregir el defecto de mayor impacto y volver a comprobar el tramo afectado. Antes de un render largo, medir cuadros representativos y explicar el costo estimado y sus límites.
6. Entregar archivos, vista previa y parámetros necesarios para reproducir el resultado; indicar qué se inspeccionó y qué sigue provisional.

## Reglas técnicas que cambian decisiones

- Separar cámara, movimiento rígido de cabeza y expresión facial. Los landmarks no reconstruyen automáticamente una cabeza exacta ni garantizan estabilidad temporal.
- Para retoque facial, conservar rasgos y expresión salvo transformación solicitada. Separar piel, cambio de edad y reemplazo dental. Dientes superiores siguen el maxilar/cabeza; inferiores, la mandíbula. Verificar labios, lengua, encías y oclusiones cuadro a cuadro.
- Mantener identidad y orden de vértices al transferir shape keys. Remeshing y retopología requieren una estrategia de transferencia si ya existen deformaciones o UV.
- Fijar fps y correspondencia de cuadros antes de tracking, animación y cachés. No confundir 24 fps de salida con 24 poses distintas por segundo.
- Mantener trazabilidad de espacios de color, alpha y distorsión de lente. Evitar aplicar dos veces una transformación de visualización o una premultiplicación.
- No imponer una luz de tres puntos sobre un plano cuya iluminación real es otra. AO puede ayudar a describir contacto, pero no reemplaza las sombras y los rebotes del plano.
- Verificar APIs y opciones contra la versión instalada. Esta investigación tomó como referencia Blender 4.5 LTS; latest puede corresponder a otra versión.

## Citar sin exagerar la evidencia

Usar el registro de [fuentes](references/fuentes.md), con título, autor/organización, edición o versión y sección. Vincular directamente el manual que respalda la afirmación; no dar una lista genérica como sustituto de citas por tema.

Las referencias distinguen contenido consultado, extracto indexado, índice y ficha bibliográfica. No afirmar lectura integral de un libro comercial, inventar páginas o tratar una recomendación de lectura como demostración de una receta. Para una cita textual o un detalle de implementación nuevo, abrir la sección correspondiente. Revalidar interfaces y capacidades que puedan cambiar.

Los ejercicios y casos de esta skill son propuestas propias basadas en los fundamentos citados, no ejemplos extraídos de los libros. No atribuirles resultados medidos hasta ejecutarlos.

## Marketplace notice

Experimental skill: it can fail or produce incorrect results. Read [limitations](NOTICE.txt) and [usage terms](LICENSE.txt). This is an agent workflow skill, not a standalone video generator. Requires your footage, licensed assets and suitable production software. Rendering quality, tracking stability and completion time are not guaranteed.
