# Aprendizaje y MVP — Reclamos con seguimiento (indumentaria online)

## 1. Experimento

## Lo que entiendo de su experimento

- Querían comprobar: que un flujo de reclamo con seguimiento transparente a lo largo del tiempo (tipo "delivery tracking") aumenta la disposición del cliente a volver a comprarle a la marca, comparado con un proceso sin seguimiento (WhatsApp/mail). Es la Hipótesis de Valor del Canvas.
- El criterio de éxito era: al menos 3 de 5 participantes completan el flujo de punta a punta, declaran mayor disposición a recomprar y aceptan ser recontactados. Las tres condiciones debían darse juntas en la misma persona.
- Construyeron o probaron: una landing con seguimiento simulado (formulario, vista de estado Recibido → En revisión → Resuelto, encuesta de cierre). Los estados se actualizaban a mano. Participaron 3 personas reales con un reclamo real o reciente.
- El resultado registrado fue: 3/3 completaron el flujo, 3/3 lo calificaron "mejor" que su experiencia previa, 2/3 declararon mayor disposición a recomprar y aceptaron recontacto. Solo 2/3 cumplieron las tres condiciones juntas.

## Chequeo rápido

- Hipótesis definida antes de probar: Sí
- Criterio definido antes de probar: Sí
- Hay resultados u observaciones: Sí
- Estado de la iteración: lista para analizar

## 2. Resultado

| Qué pasó | Cómo lo sabemos |
|---|---|
| 3 de 3 participantes completaron el formulario, vieron el estado "Resuelto" y respondieron la encuesta de cierre. | Registro de los casos RC-G429, RC-WSBB y RC-F3S9 y panel "Equipo". |
| 2 de 3 declararon mayor disposición a recomprar y aceptaron recontacto. El tercero valoró el proceso como "mejor", pero su disposición quedó "igual" y no aceptó recontacto. | Respuestas de la encuesta de cierre. |
| Los 3 estados se actualizaron casi en la misma sesión, no en días distintos como preveía el diseño. | Confirmación del equipo. No se registraron fechas de cada cambio de estado. |

- Resultado frente al criterio: no se alcanzó (2 de 3 cumplieron las tres condiciones juntas; el criterio exigía al menos 3).
- Algo que salió distinto de lo esperado: el seguimiento no ocurrió a lo largo de varios días, así que el mecanismo central de la hipótesis no llegó a probarse tal como estaba diseñado. Además, la Hipótesis de Problema sigue inconclusa: las entrevistas a marcas de la Clase 4 fueron simuladas.

## 3. Aprendizaje

- Aprendimos que: el flujo funciona de punta a punta sin errores técnicos y que los 3 participantes lo percibieron mejor que su experiencia previa. Aun así, esa mejor percepción no se tradujo siempre en mayor intención de recompra.
- Todavía no sabemos si: el seguimiento distribuido en varios días reales (y no solo la transparencia del proceso) es lo que aumenta la disposición a recomprar. Tampoco sabemos si las marcas reales reconocen el problema.

## 4. Decisión

- Elegimos: **Arreglar la prueba**.
- Porque: el resultado quedó afectado por un error de ejecución (estados actualizados en la misma sesión), no por la hipótesis. Repetir igual repetiría el sesgo.
- Próximo paso: repetir con 2-3 casos nuevos usando la misma herramienta, el mismo criterio y la misma encuesta. Los estados deben actualizarse en al menos 2 días calendario distintos antes de "Resuelto", y hay que registrar la fecha de cada cambio.

## 5. Punto de partida del MVP

- Usuario: persona que compró indumentaria online y tuvo un problema de talle o calidad con su compra.
- Situación: quiere reclamar o devolver, pero el proceso le exige tiempo, paciencia y escribir varias veces por WhatsApp o mail, sin saber en qué estado está su caso.
- Valor que queremos entregar: reducir la incertidumbre y la fricción del reclamo para que el cliente no abandone la marca aunque el problema se resuelva.
- Una sola cosa que el MVP debe permitir hacer: reportar un reclamo y ver su estado actualizado hasta la resolución.
- Qué vamos a medir cuando
