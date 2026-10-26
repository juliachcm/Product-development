# Pruebas y mejoras del MVP — Seguimiento de reclamos

## 1. Contexto

- **Equipo y fecha:** 4 integrantes · 26/10/2026.
- **Usuario y problema:** persona que compró indumentaria online y tuvo un problema de entrega, talle, calidad, cambio o devolución. Hoy debe repetir mensajes por WhatsApp o mail sin saber en qué estado está su caso.
- **Acceso al MVP:** https://ai.studio/apps/4fa275ff-ef37-4cd1-a99d-5dd51cab1a69 (app "Seguimiento de Reclamos", marca de demostración "Valia Studio"). Versión probada: **nueva** (reporte en pasos cortos y prioridad calculada). Detalle en `mvp.md`.

## 2. Tarea, finalización y ayuda

- **Tarea dada (ronda 1):** "Completá el reporte como si fuera el problema más común que tenés cuando comprás online."
- **Tarea propuesta para la ronda 2** (describe el objetivo, no dónde tocar): "Compraste una prenda y llegó con un problema. Lo necesitás resuelto esta semana. Usá esta página para reportarlo y enterarte de cómo sigue."
- **Resultado observable:** la persona llega a ver su código RC-XXXX y el estado "Recibido". Para el valor, responde la encuesta de cierre cuando el caso llega a "Resuelto".
- **Cuenta como ayuda:** que el equipo explique, indique dónde tocar o responda una pregunta sobre qué escribir. Si la ayuda ocurre, no cuenta como finalización autónoma.
- **Fin del intento:** éxito (ve su código), abandono o 10 minutos sin avanzar.

## 3. Métricas

| Métrica | Cómo se mide | Criterio exploratorio | Qué decisión informa |
| --- | --- | --- | --- |
| **Éxito de la tarea** | Participantes que ven su código / participantes que intentan (primer intento por persona y versión). | Al menos 4 de 5. | Si es menor, ver en qué paso abandonan y corregir ese paso. |
| **Autonomía** | Participantes que completan sin ayuda / participantes que intentan. Se anota cada duda o pregunta. | Al menos 4 de 5 sin ayuda y sin preguntas. | Qué textos o pasos hay que simplificar. |
| **Valor** | Tras llegar a "Resuelto", declaran mayor disposición a recomprar que en su experiencia previa y aceptan recontacto (encuesta de cierre). Se les avisa de la encuesta. | Al menos 3 de 5, como en la Clase 5. | Si el seguimiento empieza a producir confianza o solo es una mejora de interfaz. |

Con muestras pequeñas se informa "X de N", sin generalizar. Si nadie llega a la encuesta, el valor es **"no medido"**.

## 4. Registro de participantes (versión nueva)

| ID | ¿Segmento? | Versión | ¿Intentó? | ¿Completó? | ¿Sin ayuda? | Valor | Dificultad y ayuda recibida |
| --- | --- | --- | --- | --- | --- | --- | --- |
| U1 | Sí: persona con malas experiencias de postventa online | Nueva | Sí | Sí (caso RC-23BC, que figura "Resuelto") | Sí, con una duda | No medido: no completó la encuesta, porque no se le avisó | Mucho texto; doble mensaje; "¿Cuándo te lo prometieron?" le resultó raro; tardó en cargar |

**Resultado ronda 1: éxito 1 de 1, autonomía 1 de 1 (con una duda), valor no medido.** Con una persona no se puede generalizar.

**Observaciones de U1**
- No le gustó el diseño: tiene mucho texto y le resultó confuso al principio.
- Se detuvo en "¿Cuándo te lo prometieron?", la entendió por contexto y siguió sola. Propone "¿Para cuándo era tu pedido?" y un lenguaje más simple y directo.
- Le confundió el doble mensaje: el automático de arriba y la nota del equipo.
- Pidió recibir avisos del estado sin entrar a la web, y una respuesta del equipo.
- En su caso (talle que no coincide con la tabla y material distinto a lo prometido) cree que hace falta un ida y vuelta de preguntas y opciones, no solo un formulario.
- No completó la encuesta por falta de ganas y porque no se le avisó.
- La captura del caso muestra "Pedido ##1160" con dos numerales: puede ser un error de la app o de lo que se escribió.

## 5. Dificultad priorizada

| Hecho (observado) | Posible causa (a comprobar) | Mejora |
| --- | --- | --- |
| Mucho texto, doble mensaje, una pregunta confusa y lenguaje poco directo; duda en un paso. | Textos largos y formulaciones poco claras; mensajes de estado y nota del equipo juntos. | Simplificar textos, reformular la pregunta y separar claramente el estado de la nota del equipo. |

**Elegida: simplificar los textos y la pregunta.** Es lo que más apareció (varios comentarios), frena la autonomía y es barata de corregir y de volver a probar. Las otras dificultades quedan registradas abajo y no se mezclan en esta ronda.

**Pedido a la IA (para pegar en AI Studio)**

> Nuestro usuario es una persona que compró indumentaria online y quiere reportar un problema, cambio o devolución. Probamos la versión nueva con 1 persona del segmento. Observamos: tiene mucho texto, el mensaje automático y la nota del equipo se confunden, y "¿Cuándo te lo prometieron?" le resultó raro. Elegimos trabajar sobre esto porque frena que el reporte se complete sin dudas. Ayudanos a analizar posibles causas y proponé hasta tres cambios pequeños. Antes de modificar, discutamos las alternativas.

Después de elegir:

> Implementá [cambio elegido]. Conservá el reporte en pasos, el código RC-XXXX, la prioridad calculada y todo lo que ya funciona. Criterio de aceptación: una persona nueva completa el reporte sin hacer ninguna pregunta. Probá el recorrido principal y un caso de error. Indicá qué verificaste y qué sigue pendiente de prueba con personas.

## 6. Cambio implementado y verificación técnica

**[PENDIENTE]** Todavía no se implementó. Registrar: qué se cambió, versión nueva y qué se verificó (recorrido principal y un caso de error).

## 7. Comparación antes y después

| Métrica | Antes (versión nueva, 1 persona) | Después | Qué aprendimos y qué limita la comparación |
| --- | --- | --- | --- |
| Éxito | 1 de 1 | **[PENDIENTE]** | La muestra es de una persona; conviene personas nuevas, porque quien ya conoce el recorrido sesga el resultado. |
| Autonomía | 1 de 1, con una duda | **[PENDIENTE]** | Igual. |
| Valor | No medido | **[PENDIENTE]** | Avisar de la encuesta y esperar a que el caso llegue a "Resuelto". |

Esta comparación será exploratoria: no demuestra por sí sola que el cambio causó el resultado.

## 8. Próxima incertidumbre

- **Incertidumbre:** si, con textos más simples, una persona nueva completa el reporte sin preguntas, y si el seguimiento con avisos mueve su disposición a recomprar.
- **Acción más barata:** repetir la prueba con 2 a 4 personas nuevas del segmento, con la tarea propuesta, avisándoles de la encuesta de cierre.
- **Responsable y momento:** las 4 integrantes, junto con las entrevistas de precio de la semana del 26/10 al 01/11/2026 **[CONFIRMAR]**.

## Mejoras a evaluar en próximas iteraciones con IA

Quedan registradas para iterar después, de a una por vez y con evidencia:

1. **Avisos de estado fuera de la web** (mail o WhatsApp): primero manuales con `mailto:` y `wa.me`; automáticos solo más adelante.
2. **Ida y vuelta con opciones** para cambios, devoluciones y reembolsos, porque algunos casos no se resuelven sin preguntarle a la persona qué prefiere.
3. **Velocidad de carga:** U1 notó que tardó.
4. **Numeral duplicado en "Pedido ##1160":** revisar si es un error de la app.
5. **Pesos de la prioridad:** "cambio/devolución + esta semana" dio 75 puntos y quedó en rojo; revisar con más casos si el rojo pierde utilidad.
6. **Avisar de la encuesta de cierre** al terminar el seguimiento, desde el proceso de prueba y desde la app.
