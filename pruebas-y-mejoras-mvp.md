# Clase 8 · Pruebas y mejoras del MVP

> Estado: borrador. Los resultados de pruebas con personas están pendientes y se completan solo con observaciones reales.

- **Equipo y fecha:** [COMPLETAR]
- **Usuario y problema:** persona que compró indumentaria online y tuvo un problema de talle o calidad; quiere reclamar pero debe repetir mensajes por WhatsApp o mail sin saber en qué estado está su caso.
- **MVP:** app "Seguimiento de Reclamos" (Google AI Studio, marca de demostración "Valia Studio"). Enlace: [COMPLETAR]. Versión inicial = Clase 7.
- **Tarea:** "Compraste una prenda online y no era como esperabas (talle o calidad). Usá esta versión para presentar tu reclamo y después averiguar en qué estado está."
- **Inicio:** la persona abre el enlace.
- **Completó:** reportó el reclamo, obtuvo su código RC-XXXX y pudo ver el estado de su caso.
- **Cierre:** éxito, abandono o límite de 10 minutos.
- **Qué cuenta como ayuda:** cualquier indicación del equipo sobre dónde tocar, qué escribir o cómo seguir. Con ayuda, el intento cuenta como completado pero no autónomo.
- **Funcional / manual / simulado:**
  - Funciona: formulario, código, seguimiento con fecha y hora, encuesta. El cambio de estado falló el 19/10 [CONFIRMAR si ya se arregló].
  - Manual: cambios de estado y avisos por WhatsApp/mail.
  - Simulado: marca "Valia Studio" y datos de ejemplo.

## Plan de medición

| Métrica | Fórmula/unidad | Fuente y momento | Criterio exploratorio | Decisión que informa |
| --- | --- | --- | --- | --- |
| Éxito | Completan / intentan (primer intento por persona y versión) | Observación y registro manual, durante la prueba | 4 de 5 | Si no se alcanza: revisar dónde se traban y priorizar esa dificultad |
| Autonomía | Completan sin ayuda / intentan | Observación y registro de ayudas, durante la prueba | 4 de 5 | Si no se alcanza: mejorar instrucciones, textos o interacciones |
| Valor (proxy: reducción de incertidumbre) | Pueden decir correctamente en qué estado está su caso sin preguntar / completan | Pregunta de cierre, justo después de la tarea | 4 de 5 | Si no se alcanza: el seguimiento no comunica bien el estado |
| Valor real (recompra / no abandono) | Disposición a recomprar y recontacto aceptado | No medido en esta clase | n/a | Requiere seguimiento posterior: [definir con quién, dónde, cuándo y cómo] |

Notas:
- La métrica de valor es un proxy: no demuestra que el cliente deje de abandonar la marca.
- Con muestras chicas se informa "4 de 5", sin generalizar. Si nadie intentó: "no medido".
- Compañeros fuera del segmento sirven para detectar dificultades de uso, no para demostrar valor ni demanda.

## Registro de pruebas

| ID | Perfil/segmento | Versión | Intentó | Completó | Sin ayuda | Valor/unidad o no medido | Dificultad y ayuda |
| --- | --- | --- | --- | --- | --- | --- | --- |
| U1 | Por completar | Inicial | Por completar | Por completar | Por completar | Por completar | Por completar |
| U2 | Por completar | Inicial | Por completar | Por completar | Por completar | Por completar | Por completar |
| U3 | Por completar | Inicial | Por completar | Por completar | Por completar | Por completar | Por completar |

Las pruebas entre integrantes del equipo (Clase 7) y las pruebas técnicas con IA no cuentan como participantes.

## Aprendizaje e iteración

- **Hechos observados (Clase 7, prueba entre pares):**
  - 16/10: se perdió un caso (se guardaba solo en el dispositivo) y el asistente dio error 503 una vez.
  - 19/10: "Pasar a En revisión" no cambió el estado y apareció un error nuevo en consola (caso RC-B1BM).
- **Posible causa:** sin determinar. [Pegar mensaje exacto de consola]
- **Prioridad candidata:** arreglar el cambio de estado, porque sin eso nadie llega a "Resuelto". Es un problema de funcionamiento; la dificultad priorizada con evidencia de personas queda pendiente hasta la primera ronda.
- **Pedido a la IA y decisión del equipo:** [COMPLETAR]
- **Cambio realizado y verificación técnica:** [COMPLETAR]

## Comparación

| Métrica | Antes (n y resultado) | Después (n y resultado) | Interpretación y límites |
| --- | --- | --- | --- |
| Éxito | No medido | No medido | Sin segunda ronda todavía |
| Autonomía | No medido | No medido | Sin segunda ronda todavía |
| Valor (proxy) | No medido | No medido | Sin segunda ronda todavía |

## Próximo paso

- **Incertidumbre pendiente:** si el seguimiento distribuido en varios días (no solo la transparencia) sube la disposición a recomprar, y si las marcas reales reconocen el problema (las entrevistas de la Clase 4 fueron simuladas).
- **Acción más barata:** 1) arreglar el cambio de estado, 2) correr la tarea sin indicaciones con 3 a 5 personas, 3) combinar con la repetición de la Clase 5 (estados en al menos 2 días calendario distintos, registrando la fecha de cada cambio). Responsable y fecha: [COMPLETAR]
- **Qué decidir según el resultado:** si éxito o autonomía quedan bajo el criterio, mejorar la dificultad más bloqueante y volver a probar con personas nuevas; si el recorrido funciona, pasar a medir valor real con seguimiento posterior.
