# Nuestro primer MVP

- **Usuario y situación:** persona que compró indumentaria online y tuvo un problema de talle o calidad; quiere reclamar, pero debe repetir mensajes por WhatsApp o mail sin saber en qué estado está su caso. También usa la app el equipo de una marca chica.
- **Valor y acción central:** reducir la incertidumbre y la fricción del reclamo para que el cliente no abandone la marca aunque se resuelva. Acción central: reportar un reclamo y ver su estado hasta la resolución.
- **Acceso o forma de ejecución:** app "Seguimiento de Reclamos" en Google AI Studio, con marca de demostración "Valia Studio". Enlace: **[PENDIENTE: pegar enlace de Share/Publish]**. La vista del equipo se abre con un PIN simple.
- **Recorrido:** el cliente entra → reporta el reclamo y recibe un código RC-XXXX → sigue su estado (Recibido → En revisión → Resuelto) y responde la encuesta de cierre. El equipo cambia el estado a mano y avisa al cliente.
- **Funciona / manual o simulado / fuera de alcance:** *Funciona:* formulario, código, seguimiento con fecha y hora, panel por motivo, encuesta y asistente de IA (el 19/10 el cambio de estado falla **[CONFIRMAR si ya se resolvió]**). *Manual:* cambios de estado, avisos por WhatsApp o mail y el campo "¿Volvió a comprar?". *Simulado:* marca, contacto del pie y datos de ejemplo. *Fuera:* chat con el cliente, notificaciones automáticas, login, pagos, integraciones.
- **Evidencia disponible y duda pendiente:** en la Clase 5, 2 de 3 casos cumplieron las tres condiciones del criterio y se necesitaban 3, con los estados actualizados en la misma sesión. Duda: si el seguimiento en varios días y los avisos aumentan la tranquilidad y la disposición a recomprar, y si las marcas reconocen el problema (las entrevistas de la Clase 4 fueron simuladas). Los datos se guardan sin autenticación.
- **Qué medimos:** usuarios que intentan y completan la acción; resultado útil observado. Intentos: **[N]**; llegaron a "Resuelto": **[N]**; completaron la encuesta: **[N]**.

## Prueba e iteración

- **Quién probó (rol) y tarea:** integrantes del equipo (prueba entre pares): reportar un reclamo, seguirlo y cambiar su estado desde el panel. **[PENDIENTE: prueba con otra persona sin indicaciones]**
- **Qué ocurrió y cómo lo sabemos:** el 16/10 se perdió un caso (se guardaba solo en el dispositivo) y el asistente dio error 503 una vez; el 19/10 el cambio de estado dejó de funcionar y el contador de errores subió de 2 a 3 (capturas y consola de AI Studio). Código inexistente, formulario vacío y asistente con menos de 3 casos: **[PENDIENTE: qué mostró cada uno]**.
- **Devolución concreta que dimos a la IA:** abrimos el caso RC-B1BM y apretamos "Pasar a En revisión"; esperábamos que cambiara el estado y quedara en el historial; no pasó nada y apareció un error nuevo en la consola; evidencia: capturas **[PENDIENTE: pegar el mensaje exacto]**.
- **Cambio realizado y resultado de la nueva prueba:** **[PENDIENTE]**
- **Próximo ajuste:** arreglar el cambio de estado, probar un aviso real por WhatsApp, probar con otra persona y repetir la prueba de la Clase 5 con estados en al menos 2 días distintos.
