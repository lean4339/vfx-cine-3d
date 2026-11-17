# Render y composición

## Renderizar para responder una pregunta

El path tracing estima transporte de luz mediante muestreo de caminos. El ruido depende de varianza y muestras; aumentar muestras cuesta tiempo y no arregla una cámara mal resuelta. El apartado [PBRT §13.2 — S21](https://pbr-book.org/4ed/Light_Transport_I_Surface_Reflection/Path_Tracing) desarrolla el integrador. Como referencia matemática, el error Monte Carlo suele decrecer aproximadamente con `1/sqrt(N)` bajo condiciones habituales: cuadruplicar muestras puede reducirlo a la mitad, no por cuatro.

Elegir motor según efectos requeridos y comparar un cuadro representativo. Para GPU verificar dispositivo, backend, memoria y soporte; el manual enumera opciones por fabricante/sistema, pero no garantiza que cualquier GPU sea más rápida para toda escena. [Cycles GPU Rendering — S22](https://docs.blender.org/manual/pt/4.5/render/cycles/gpu_rendering.html).

Medir tiempo y memoria en cuadros difíciles. El denoiser puede alterar textura fina o parpadear: inspeccionar la secuencia. Guardar secuencias de imágenes para reanudar un render y generar el video de revisión después. Un EXR no mejora por sí mismo una iluminación incorrecta.

## Pases y máscaras

Separar solo los controles que se utilizarán: beauty, sombra/contacto, emisión, identificadores y componentes relevantes. Cryptomatte identifica superficies renderizadas; no recorta mágicamente a Moshi en el video original. Shadow catcher ayuda a recibir interacción sobre geometría de referencia. Sus resultados y combinación dependen del motor y del pase. [Blender Passes — S23](https://docs.blender.org/manual/en/4.5/render/layers/passes.html).

Distinguir una máscara de visibilidad de un elemento de luz. La persona filmada puede requerir roto, key o segmentación con correcciones; las oclusiones entre objetos digitales pueden resolverse en 3D. No usar un pase de profundidad simple como sustituto universal de cabello, transparencias y motion blur.

## Color: preservar significado

Identificar la transformación de entrada del metraje y el espacio de trabajo. Para operaciones físicas de luz, trabajar en un espacio lineal coherente. Mantener la transformación de visualización separada del archivo de intercambio. Un EXR puede contener imagen lineal y varios canales; registrar primarias y configuración de color. [Blender Color Management — S24](https://docs.blender.org/manual/fi/4.5/render/color_management.html).

No aplicar AgX/otra transformación de apariencia dos veces. Convertir una imagen de video ya procesada a valores lineales no recupera automáticamente el rango ni deshace todo su procesamiento original. Si falta información, declarar la interpretación y verificar que el plate conserve su apariencia al atravesar el flujo sin cambios.

## Alpha y bordes

Con color premultiplicado, una operación over usa `C = Cf + (1 - af) * Cb`. Con color straight, primero corresponde ponderar el foreground por su alpha. Registrar la convención; una doble premultiplicación puede producir bordes oscuros. Al corregir color puede ser necesario desmultiplicar, corregir y premultiplicar, tratando alpha cero con cuidado. [OpenEXR Technical Introduction — S26](https://openexr.com/en/latest/TechnicalIntroduction.html).

HALF es flotante de 16 bits; FLOAT ofrece mayor rango/precisión. Decidir por canal y necesidad; profundidad u otros datos pueden necesitar precisión distinta de RGB. Mantener coherentes data window, display window y overscan.

## Acabado propuesto

1. Integrar oclusiones y contacto; verificar bordes sobre fondos claros y oscuros.
2. Igualar exposición, contraste y balance dentro del mismo flujo de color.
3. Comparar enfoque, motion blur y respuesta de lente; no aplicar doble blur al metraje.
4. Hacer limpieza/denoise solo cuando ayude; reponer grano coherente después de las operaciones espaciales principales, evitando duplicarlo en zonas intactas.
5. Revisar reproducción, cortes y entrega codificada además del máster.

Para profundizar en keying, roto, composición e integración, consultar [Steve Wright, 5.ª edición — S25](https://www.routledge.com/Digital-Compositing-for-Film-and-Video-Production-Workflows-and-Techniques/Wright/p/book/9781032417998). El orden anterior es una propuesta adaptable, no una receta atribuida al libro.

## Diagnóstico rápido

| Síntoma | Comprobar primero |
|---|---|
| Parece flotar | Perspectiva, contacto, dirección de sombra y apoyo. |
| Parece pegado | Bordes, enfoque, contraste, oclusión y movimiento relativo. |
| Cambia de color al exportar | Transformaciones duplicadas, etiquetas, rango y visualizador. |
| Parpadea | Tracking, texturas, simulación, muestras, denoise y regeneración independiente de cuadros. |
| Halo oscuro | Convención alpha, filtrado y contaminación del borde. |

Una revisión válida incluye fotogramas críticos y velocidad real. Entregar resultado y comparación; no confundir un contacto visual convincente con exactitud física total.
