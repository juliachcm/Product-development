# Diseño del experimento — Clase 5

## 1. Evidencia de partida

- **Cliente/usuario:** equipo de atención al cliente / operaciones de una marca de indumentaria online.
- **Problema de negocio (Canvas, Caja 1):** las marcas pierden clientes después de un reclamo aunque lo resuelvan bien, por la fricción del proceso.
- **Hipótesis de Problema (Caja 6), probada en Clase 4:** el equipo de la marca enfrenta reclamos donde el cliente abandona la relación aunque el problema se resuelva.
  - **Estado:** *inconclusa.* Las 5 entrevistas de Clase 4 fueron **simuladas** (marcadas explícitamente en `entrevistas-marcas.md`), no evidencia real. La señal direccional (4 de 5 confirmarían en algún grado) no puede usarse para decidir sobre la hipótesis de negocio.
  - **Decisión pendiente heredada de Clase 4:** conseguir entrevistas reales con marcas. El equipo optó por continuar por ahora con datos simulados y avanzar igual a la Clase 5, dejando explícito que esto no reemplaza esa validación pendiente.

## 2. Pregunta de aprendizaje (Clase 5)

> ¿Las personas que recorren un flujo de reclamo con seguimiento transparente en tiempo real (tipo delivery tracking) completan el recorrido de principio a fin y declaran mayor disposición a volver a comprarle a la marca, comparado con su experiencia previa sin seguimiento (WhatsApp/mail)?

Corresponde a la **Hipótesis de Valor** del Canvas (Caja 6):
> Un flujo de reclamos transparente y con seguimiento en tiempo real reduce el abandono de clientes tras un reclamo resuelto.

## 3. Experimento elegido

**Landing con seguimiento simulado + reacción diferida** — combinación de dos alternativas comparadas:

- De un *prototipo navegable* tomamos: recorrido en varios pasos y entrevista de reacción al cierre.
- De un *fake door / landing* tomamos: una sola pantalla de reporte, sin necesidad de armar múltiples vistas de antemano.

La combinación resuelve la limitación de cada alternativa por separado: el prototipo navegable no capturaba el paso del tiempo real (todo se mostraba de una sola vez); el fake door no tenía seguimiento posterior. Acá el estado avanza en días reales, no en una demo instantánea.

## 4. Partes reales y simuladas

| Parte | Real | Simulada |
|---|---|---|
| Persona que reporta y su reacción | ✅ | |
| Reclamo descripto | ✅ (puede ser un caso real o reciente de la persona) | |
| Paso del tiempo entre estados | ✅ | |
| Cambio de estado del sistema | | ✅ — lo actualiza el equipo a mano desde el panel interno, no hay lógica automática de resolución |
| Notificación de cambio de estado | | ✅ — aviso manual del equipo, no hay sistema de notificaciones real |
| Marca detrás del flujo | | ✅ — no es una marca real, se presenta honestamente como prototipo de investigación |
| Backend / base de datos de casos | Parcial | Se usa almacenamiento simple del artifact (equivalente a una planilla), no un sistema de tickets real |

## 5. Contrato experimental

| Campo | Definición |
|---|---|
| **Hipótesis** | Un flujo de reclamo con seguimiento transparente a lo largo del tiempo aumenta la disposición del cliente a volver a comprarle a la marca, comparado con un proceso sin seguimiento (WhatsApp/mail). |
| **Aprendizaje** | Si completar un reclamo con seguimiento visible genera más confianza/disposición a recomprar que la experiencia actual sin seguimiento. |
| **Participantes o escenarios** | 3 a 5 personas con un reclamo real o reciente de indumentaria online, reclutadas directamente por el equipo. No se usan personas sintéticas como evidencia — solo se usarían para depurar el instrumento antes del piloto real, si hiciera falta. |
| **Acción o resultado observable** | (1) Completan el formulario de reporte inicial. (2) Notan al menos una actualización de estado en los días siguientes. (3) Responden la encuesta de cierre comparando con su experiencia previa. |
| **Métrica** | % que completan el formulario inicial + % que declaran mayor disposición a recomprar + % que aceptan ser recontactados por la marca (proxy de comportamiento). |
| **Criterio de éxito** | Al menos 3 de 5 participantes completan el flujo de punta a punta, **y** declaran mayor disposición a recomprar, **y** aceptan ser recontactados. Las tres condiciones deben darse juntas en la misma persona — no alcanza con que se cumplan por separado en personas distintas. |
| **Duración / regla de fin** | 5 a 7 días: 1-2 días para reclutar y que reporten el caso, 2-4 días de seguimiento con al menos un cambio de estado, cierre con la encuesta. |
| **Limitación declarada** | No prueba si el proceso funciona escalado a muchos reclamos simultáneos, ni si una marca real lo adoptaría (eso es Hipótesis de Factibilidad, pendiente). "Disposición a recomprar" es autorreportada; se agregó el proxy de recontacto para no depender solo de la opinión declarada, pero sigue sin ser una compra real. |

## 6. Alcance mínimo

| Componente | Categoría |
|---|---|
| Formulario de reporte (nombre, contacto, descripción) | Imprescindible |
| Vista de estado con progreso (Recibido → En revisión → Resuelto) | Imprescindible |
| Actualización de estado en días reales | Imprescindible, motor simulado (manual) |
| Notificación de cambio de estado | Simulable (aviso manual del equipo) |
| Encuesta de cierre + checkbox de recontacto | Imprescindible |
| Backend/sistema real de tickets | Fuera de alcance |
| Login / cuenta de usuario | Fuera de alcance |
| Identidad de marca real | Fuera de alcance / simulado genéricamente |

## 7. Protocolo de ejecución

1. El equipo recluta 3-5 personas con un reclamo real o reciente.
2. Cada persona reporta su caso en la pestaña "Reportar un reclamo" y guarda su código.
3. El equipo, desde la pestaña "Equipo (uso interno)", avanza el estado de cada caso en días distintos (no todo el mismo día) y avisa manualmente por fuera de la herramienta (WhatsApp/mail) que hay novedades.
4. Al llegar a "Resuelto", la persona vuelve a la pestaña "Seguir mi reclamo", ve el estado final y completa la encuesta de cierre.
5. El equipo revisa el panel de estadísticas para comparar contra el criterio de éxito.

## 8. Decisiones humanas registradas

- Se decidió continuar con datos simulados en lugar de esperar entrevistas reales de marca, para no frenar el avance a la Clase 5 — dejando explícito que la Hipótesis de Problema sigue inconclusa.
- Se eligió la pregunta de aprendizaje B (Hipótesis de Valor) sobre A y C.
- Se compararon 3 alternativas de experimento y se decidió combinar dos de ellas en lugar de elegir una sola.
- Se mantuvo el criterio combinado (no separado en métricas independientes).
- Se agregó un proxy de comportamiento (aceptar recontacto) en lugar de depender solo de la respuesta autorreportada.
- Se aprobó el alcance mínimo antes de construir el instrumento.

## 9. Estado final (cierre Clase 5)

- **Resultado:** No respaldada por esta prueba — 2 de 3 participantes cumplieron las 3 condiciones del criterio juntas (el criterio exigía al menos 3).
- **Motivo principal:** el seguimiento no se distribuyó en días reales como preveía el diseño — se ejecutó comprimido en una sola sesión. El equipo interpretó esta corrida como una validación del funcionamiento del instrumento, no como prueba concluyente del mecanismo de "seguimiento en el tiempo".
- **Tipo de cambio decidido:** corrección de la ejecución (no pivot). Se conservan problema, Hipótesis de Valor, criterio e instrumento.
- **Decisión del equipo:** dar la prueba por cerrada sin repetir en esta sesión. La corrección (estados actualizados en días distintos) queda diseñada y lista para retomar — ver `registro-experimento.md`, sección "Iteración 1".
- **Detalle completo de la ejecución, datos y análisis:** `registro-experimento.md`.






# Registro del experimento — Clase 5 (Hipótesis de Valor)

> Completar un bloque por cada participante, a medida que se ejecuta. No completar huecos con inferencias: si un dato no se registró, dejarlo en blanco y anotarlo como dato faltante.

## Piloto (no cuenta para el criterio de éxito)

- **Dato faltante:** no quedó registrado en el chat el detalle del piloto (quién lo hizo, qué se observó). El equipo confirmó verbalmente que "probaron el recorrido y funciona", pero no se documentaron observaciones puntuales. Pendiente completar si el equipo las tiene por fuera de este registro.

---

## Ejecución real

### Caso 1 — RC-G429

- **Código del caso:** RC-G429
- **Participante:** Michelle Escobar (michelle.escobar@gmail.com)
- **Fecha de reporte:** 14-sept, 09:11 p.m.
- **Descripción del reclamo (textual):** "compre un traje de baño y después de usarlo una vez, se soltó un hilo y se rompió. Me pareció muy mala la calidad."
- **¿Completó el formulario inicial?** Sí
- **Estado final:** Resuelto
- **¿Completó la encuesta de cierre?** Sí
  - Comparación con experiencia previa: **mejor**
  - Disposición a recomprar: **igual**
  - Aceptó recontacto: **no**
- **Cumple las 3 condiciones del criterio de éxito juntas:** No (disposición no aumentó, no aceptó recontacto)
- **Dato faltante:** fechas de cada cambio de estado intermedio, tiempo total del proceso, comportamientos observados durante el uso.

### Caso 2 — RC-WSBB

- **Código del caso:** RC-WSBB
- **Participante:** Julia Chiaradia (juliach06@icloud.com)
- **Fecha de reporte:** 14-sept, 09:03 p.m.
- **Descripción del reclamo (textual):** "El talle que pedí era unitalla y no me entró, no coincidía con la tabla de medidas. Además la calidad era muy mala, a diferencia de las que se ve en las fotos."
- **¿Completó el formulario inicial?** Sí
- **Estado final:** Resuelto
- **¿Completó la encuesta de cierre?** Sí
  - Comparación con experiencia previa: **mejor**
  - Disposición a recomprar: **más**
  - Aceptó recontacto: **sí**
- **Cumple las 3 condiciones del criterio de éxito juntas:** Sí
- **Dato faltante:** fechas de cada cambio de estado intermedio, tiempo total del proceso.

### Caso 3 — RC-F3S9

- **Código del caso:** RC-F3S9
- **Participante:** Lucía Kohan (luciakohan@icloud.com)
- **Fecha de reporte:** 14-sept, 09:03 p.m.
- **Descripción del reclamo (textual):** "Compre un buzo y no era nada parecido al de la foto entonces me decepcionó y lo devolví."
- **¿Completó el formulario inicial?** Sí
- **Estado final:** Resuelto
- **¿Completó la encuesta de cierre?** Sí
  - Comparación con experiencia previa: **mejor**
  - Disposición a recomprar: **más**
  - Aceptó recontacto: **sí**
- **Cumple las 3 condiciones del criterio de éxito juntas:** Sí
- **Dato faltante:** fechas de cada cambio de estado intermedio, tiempo total del proceso.

---

## Resumen cuantitativo (tomado del panel "Equipo" del instrumento)

| Métrica | Resultado |
|---|---|
| Total de reclamos reportados | 3 |
| % que completaron el flujo de punta a punta (formulario + cierre) | 3/3 (100%) |
| % que declararon comparación "mejor" que su experiencia previa | 3/3 (100%) |
| % que declararon mayor disposición a recomprar ("más") | 2/3 (67%) |
| % que aceptaron ser recontactados | 2/3 (67%) |
| Cumplen las 3 condiciones juntas (criterio de éxito completo) | **2/3** |

## Errores y anomalías (conservar, no descartar)

- **Anomalía de contexto (confirmada por el equipo):** los 3 casos se actualizaron por los 3 estados (Recibido → En revisión → Resuelto) casi en la misma sesión, no distribuidos en días distintos como preveía el contrato experimental. El mecanismo central de la Hipótesis de Valor — que el seguimiento *a lo largo del tiempo* genera confianza — no llegó a ponerse a prueba tal como estaba diseñado. Lo que sí se probó fue una versión comprimida, más parecida a una demo instantánea (opción "prototipo navegable" del Paso 3) que al experimento combinado acordado.

- RC-G429 completó todo el flujo y calificó el proceso como "mejor" que su experiencia previa, pero eso **no** se tradujo en mayor disposición a recomprar ni en aceptar recontacto — es el único caso donde el proceso se percibió positivo pero no movió la intención de recompra. No se infiere la causa; no fue preguntado en la encuesta.
- Los 3 casos muestran motivos de reclamo distintos entre sí (calidad de tela, talle no coincidente, producto distinto a la foto) — no permite aislar si el efecto del seguimiento varía según el tipo de motivo.

## Datos faltantes o no registrados

- No se registraron las fechas de cada cambio de estado intermedio (Recibido → En revisión → Resuelto) para ningún caso — no sabemos si el seguimiento ocurrió realmente distribuido en varios días o se actualizó todo junto.
- No se registró el detalle del piloto.
- No se registraron comentarios libres opcionales de la encuesta de cierre (si los hubo).
- Faltan 0 a 2 participantes para llegar al máximo de 5 previsto en el contrato (el mínimo de 3 sí se alcanzó).

---

## Iteración 1

- **Experimento anterior:** Landing con seguimiento simulado + reacción diferida, ejecutado con 3 casos reales (RC-G429, RC-WSBB, RC-F3S9).
- **Resultado:** No respaldada por esta prueba (2 de 3 cumplieron las 3 condiciones del criterio juntas; el criterio exigía al menos 3).
- **Evidencia producida:** 3/3 completaron el flujo de punta a punta sin errores técnicos reportados. 3/3 calificaron el proceso como "mejor" que su experiencia previa. 2/3 declararon mayor disposición a recomprar y aceptaron ser recontactados; 1/3 calificó el proceso positivo pero no aumentó su disposición ni aceptó recontacto.
- **Por qué no sirve seguir insistiendo de la misma manera:** el equipo confirmó que los 3 estados (Recibido → En revisión → Resuelto) se actualizaron casi en la misma sesión, no distribuidos en días reales como preveía el contrato. Repetir la prueba de la misma forma repetiría ese mismo sesgo de ejecución.
- **Supuesto que quedó cuestionado:** no la Hipótesis de Valor en sí — el equipo interpretó esta corrida principalmente como una prueba de funcionamiento del instrumento (MVP), no como una prueba concluyente del mecanismo de "seguimiento a lo largo del tiempo". Queda pendiente si ese mecanismo específico (vs. solo la transparencia del proceso) es lo que mueve la disposición a recomprar.
- **Qué conservamos:** problema, Hipótesis de Valor, criterio de éxito, instrumento tal como está construido.
- **Qué modificamos:** el protocolo de ejecución — exigir que las actualizaciones de estado ocurran en días distintos, no en la misma sesión.
- **Tipo de cambio:** corrección (no iteración de método ni pivot de hipótesis).
- **Próximo experimento:** misma herramienta (`reclamos-seguimiento.html`), con 2-3 casos nuevos o reabriendo el seguimiento si corresponde, actualizando el estado en al menos 2 días distintos antes de llegar a "Resuelto".
- **Qué evidencia diferente esperamos obtener:** si la disposición a recomprar sube más cuando el seguimiento realmente toma varios días, en comparación con esta corrida donde todo se resolvió de forma casi inmediata.
- **Nuevo contrato experimental:** igual al original (Paso 4), agregando una condición de ejecución explícita: mínimo 2 actualizaciones de estado en días calendario distintos antes del cierre. El equipo decidió **no ejecutar esta corrección ahora** — queda diseñada y lista para retomar cuando el equipo lo decida (posiblemente en la Clase 6).

