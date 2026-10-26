# Nuestro primer MVP

- **Usuario y situación:** persona que compró indumentaria online y tuvo un problema de entrega, talle, calidad, cambio o devolución. Quiere reclamar, pero hoy debe repetir mensajes por WhatsApp o mail sin saber en qué estado está su caso. También usa la app el equipo de una marca chica.
- **Valor y acción central:** reducir la incertidumbre y la fricción del reclamo para que el cliente no abandone la marca aunque el problema se resuelva. Acción central: **reportar un caso y ver su estado hasta la resolución**.
- **Acceso o forma de ejecución:** app "Seguimiento de Reclamos" en Google AI Studio, con marca de demostración "Valia Studio". Enlace: **https://ai.studio/apps/4fa275ff-ef37-4cd1-a99d-5dd51cab1a69**. La vista del equipo se abre con un PIN simple. Los casos se guardan en Firestore.
- **Recorrido:** el cliente elige qué pasó entre 5 opciones (No llegó, Llegó roto o equivocado, No me queda, Quiero cambiarlo o devolverlo, Otro) → ingresa número de pedido y mail (obligatorios) y, si quiere, WhatsApp → el caso se crea y recibe un código RC-XXXX → de forma opcional completa para cuándo lo necesita, fecha prometida, fecha de compra, texto y fotos (puede saltar este paso) → ve el estado Recibido y puede pedir hablar con un asesor → sigue su caso (Recibido → En revisión → Resuelto) y responde la encuesta de cierre. El equipo ve los casos ordenados por prioridad, cambia el estado a mano y avisa al cliente con botones de mail o WhatsApp con el mensaje armado.
- **Funciona / manual o simulado / fuera de alcance:**
  - *Funciona (probado por el equipo con datos de prueba):* reporte en pasos, validación de mail, código RC-XXXX, creación del caso al terminar el paso 2, prioridad calculada 🔴🟡🟢 con motivo en una línea, tarjeta de "Casos rojos sin atender", palabras clave editables, "Pidió asesor" que sube el caso a rojo, panel por motivo, encuesta y asistente de IA **[CONFIRMAR si el cambio de estado y el asistente andan hoy]**.
  - *Manual:* cambios de estado, avisos por mail o WhatsApp (los envía una persona al apretar el botón) y el campo "¿Volvió a comprar?". **[CONFIRMAR que ambos botones abren la app]**
  - *Simulado:* marca "Valia Studio", número de contacto y datos de ejemplo.
  - *Fuera de alcance:* chat con el cliente, notificaciones automáticas, login, pagos, integraciones, llamada con IA, exportar CSV, IA que clasifique o escriba sola, planes por marca.
  - *Limitación:* la app no tiene login. AI Studio advirtió que el listado de casos podría quedar accesible a nivel API y que el PIN es solo una barrera de interfaz. Por eso se prueba únicamente con datos que no son personales.
- **Evidencia disponible y duda pendiente:** en la Clase 5, 2 de 3 casos cumplieron las tres condiciones del criterio y se necesitaban 3, con los estados actualizados en la misma sesión. Las entrevistas a marcas de la Clase 4 fueron simuladas. Duda: si el seguimiento en varios días, los avisos y el orden por prioridad aumentan la tranquilidad y la disposición a recomprar, y si las marcas reconocen el problema.
- **Qué medimos:** usuarios que intentan y completan la acción; resultado útil observado. Intentos: **[N]**; llegaron a "Resuelto": **[N]**; completaron la encuesta: **[N]**; casos que dejaron el paso 3 sin completar: **[N]**.

## Prueba e iteración

- **Quién probó (rol) y tarea:** integrantes del equipo (prueba entre pares), con datos de prueba. Tarea: reportar un caso, seguirlo y cambiar su estado desde el panel. **[PENDIENTE: prueba con otra persona, sin indicaciones]**
- **Qué ocurrió y cómo lo sabemos:**
  - 16/10: se perdió un caso porque se guardaba solo en el dispositivo (se resolvió conectando Firestore) y el asistente dio error 503 una vez.
  - 19/10: el cambio de estado dejó de funcionar y el contador de errores subió de 2 a 3 (capturas y consola de AI Studio).
  - Después de las últimas mejoras, el equipo repitió pruebas con cinco casos sin datos personales: "No llegó" + "Hoy" queda en rojo con el motivo "No llegó + necesita hoy"; "Talle" + "Sin apuro" queda en verde; saltar el paso 3 conserva el caso con su código; un mail mal formado no deja avanzar; "Pidió asesor" lo sube a rojo y queda en el historial.
- **Devolución concreta que dimos a la IA:**
  1. En el caso RC-B1BM apretamos "Pasar a En revisión"; esperábamos que cambiara el estado y quedara en el historial; no pasó nada y apareció un error nuevo en la consola.
  2. Los botones de mail y WhatsApp armaban el texto pero no abrían la app. Pedimos que abrieran `mailto:` y `wa.me` en pestaña nueva.
  3. El teléfono visible arriba hacía que llamaran antes de completar el reporte. Pedimos sacarlo de la parte superior.
- **Cambio realizado y resultado de la nueva prueba:** reporte en pasos cortos con el caso creado al terminar el paso 2, y prioridad calculada visible solo para el equipo (problema, urgencia, fecha prometida vencida, palabras clave, "Pidió asesor"). Resultado de la nueva prueba: ver los cinco escenarios de arriba. **[AGREGAR qué pasó con el cambio de estado y los botones]**
- **Próximo ajuste:** probar con otra persona sin indicaciones y comparar cuántas completan el reporte frente a cuántas intentan contactar por otro medio; probar un aviso real por WhatsApp; repetir la prueba de la Clase 5 con estados en al menos 2 días distintos. 
