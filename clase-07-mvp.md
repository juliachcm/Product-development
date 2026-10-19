# Nuestro primer MVP

- **Usuario y situación:** persona que compró indumentaria online y tuvo un problema de talle o calidad. Quiere reclamar, pero el proceso le exige tiempo y mensajes repetidos por WhatsApp o mail, sin saber en qué estado está su caso. Segundo usuario: el equipo de una marca chica que gestiona esos reclamos.
- **Valor y acción central:** reducir la incertidumbre y la fricción del reclamo para que el cliente no abandone la marca aunque el problema se resuelva. Acción central: reportar un reclamo y ver su estado hasta la resolución.
- **Acceso o forma de ejecución:** app "Seguimiento de Reclamos" hecha en Google AI Studio, con una marca de demostración ("Valia Studio"). Enlace: **[PENDIENTE: pegar enlace de Share/Publish]**. La vista del equipo se abre con un PIN simple (no es seguridad real). Cuando la app no logra conectarse a la base, muestra el aviso "Datos de demostración: se guardan solo en este dispositivo".
- **Recorrido:** el cliente entra → reporta el reclamo (motivo, datos, descripción, fotos opcionales) → recibe un código RC-XXXX → sigue el estado (Recibido → En revisión → Resuelto) → responde la encuesta de cierre. El equipo ve la lista de casos, abre el detalle, cambia el estado a mano y avisa al cliente.
- **Funciona / manual o simulado / fuera de alcance:**
  - *Funcionó en la prueba del 16/10:* formulario, código, seguimiento con fecha y hora, cambio de estado, panel del equipo, clasificación por motivo, encuesta de cierre, campo "¿Volvió a comprar?", asistente de IA (con un error de saturación 503 y luego funcionó).
  - *Falla en la versión del 19/10:* el cambio de estado desde el panel no hace nada. **[CONFIRMAR si ya se resolvió]**
  - *Manual:* cambios de estado, aviso al cliente (el botón abre WhatsApp o mail con el mensaje redactado; lo envía una persona), "¿Volvió a comprar?".
  - *Simulado:* marca "Valia Studio", datos de contacto del pie y datos de ejemplo.
  - *Fuera de alcance:* chat con el cliente, notificaciones automáticas, login, pagos, integraciones con tiendas, embeberlo en la web de una marca, exportar CSV.
- **Evidencia disponible y duda pendiente:** en la prueba de la Clase 5 (3 casos reales) 2 de 3 cumplieron las tres condiciones del criterio, y se necesitaban 3. Esa prueba no se considera concluyente porque los estados se actualizaron en la misma sesión. Dudas abiertas: si un seguimiento repartido en varios días, con avisos, aumenta la tranquilidad y la disposición a recomprar; y si las marcas reconocen el problema (las entrevistas de la Clase 4 fueron simuladas). Limitación: los datos se guardan sin autenticación y el PIN no protege la base.
- **Qué medimos:** usuarios que intentan y completan la acción; resultado útil observado (comparación con la experiencia anterior, disposición a recomprar, aceptación de recontacto, "¿sintió que había alguien pendiente?", tiempo hasta el primer cambio de estado).
  - Registro manual de la prueba: reclamos iniciados: **[N]**; llegaron a "Resuelto": **[N]**; completaron la encuesta: **[N]**.

## Prueba e iteración

- **Quién probó (rol) y tarea:** integrantes del equipo (prueba entre pares, no con el segmento objetivo): reportar un reclamo, seguirlo y cambiar su estado desde el panel (16/10 y 19/10). **[PENDIENTE: prueba con otra persona sin instrucciones paso a paso]**
- **Qué ocurrió y cómo lo sabemos:**
  - 16/10, primera versión: el asistente de IA falló con un error 503 (servicio saturado) y después funcionó; un caso cargado se perdió porque los datos se guardaban solo en el dispositivo; el diseño resultó monótono y difícil de distinguir. Lo sabemos por capturas y la consola de AI Studio.
  - 19/10, segunda versión: mejoró la navegación (secciones, colores por estado y motivo, botón "Avisar al cliente"), pero el cambio de estado dejó de funcionar y el contador de errores subió de 2 a 3.
  - Casos borde: código inexistente: **[PENDIENTE: qué mostró]**; formulario con campos obligatorios vacíos: **[PENDIENTE: qué mostró]**; asistente con menos de 3 casos: **[PENDIENTE: qué mostró]**.
- **Devolución concreta que dimos a la IA:**
  - Qué hicimos: abrimos el caso RC-B1BM en estado Recibido y apretamos "Pasar a En revisión" (también probamos "Marcar como resuelto" en otro caso).
  - Qué esperábamos: que el estado cambiara y quedara registrado en el historial con fecha y hora.
  - Qué pasó: no pasó nada y apareció un error nuevo en la consola.
  - Evidencia: capturas del panel y de la consola. **[PENDIENTE: pegar el mensaje de error exacto]**
  - Antes pedimos también guardar los reclamos en una base compartida (Firestore) y mejorar el diseño, los avisos y los reintentos del asistente.
- **Cambio realizado y resultado de la nueva prueba:** **[PENDIENTE]**
- **Próximo ajuste:** 1) arreglar el cambio de estado (posible desalineación entre las reglas de Firestore y los campos nuevos); 2) probar un aviso real por WhatsApp; 3) probar con otra persona; 4) repetir la prueba de la Clase 5 con estados actualizados en al menos 2 días distintos y con la nueva pregunta de tranquilidad.
