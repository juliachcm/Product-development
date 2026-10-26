# Economía del producto — Seguimiento de reclamos (indumentaria online)

- **Fecha, moneda y período:** 26/10/2026 · pesos argentinos (ARS) · por mes.
- **Usuario, valor y evidencia disponible:** compradora de indumentaria online con un problema de talle, calidad, entrega, cambio o devolución. El valor es reducir su incertidumbre y fricción, y que la marca no pierda al cliente ni la confianza. Evidencia: prueba de la Clase 5 con 3 compradoras (2 de 3 cumplieron las tres condiciones; el criterio pedía 3, con estados actualizados en la misma sesión). Las entrevistas a marcas de la Clase 4 fueron simuladas.
- **Quién pagaría y por qué:** la marca/tienda (**hipótesis**, sin evidencia de pago). Incentivo principal: retener al cliente tras un reclamo con buena experiencia y atención. Secundario y diferencial: reclamos ordenados por motivo y por prioridad (rojo/amarillo/verde).
- **Unidad económica:** una marca por mes, con planes tipo Tiendanube. Casos ilimitados en todos los planes; se limita solo lo que cuesta (IA, avisos).
  - **Gratis:** formulario, estados, lista y clasificación básica. Se cuenta como costo de captación.
  - **Pro (PyMEs):** se calcula abajo.
  - **Avanzado:** solo visión, sin precio. Requeriría servidor, mails o WhatsApp automáticos y más IA, fuera de AI Studio.

## Números iniciales (plan Pro, por marca por mes)

| Concepto | Importe y unidad | Tipo | Fuente o motivo |
| --- | --- | --- | --- |
| Ingreso | $25.000 | Estimación | Supuesto del equipo, como fracción de lo que paga una PyME por su plataforma. |
| Soporte del equipo | 3 h × $1.956 = $5.868 | Horas: estimación. Valor hora: referencia (piso) | Salario mínimo por hora desde 01/10/2026 (iProfesional); es un piso, no un sueldo de mercado. |
| IA | 300 consultas × ~US$ 0,0012 = US$ 0,36 (hasta US$ 0,68 con otro modelo) ≈ $566 a $1.069 | Estimación de consumo; precio de referencia oficial | 100 casos × 3 consultas; 1.500 tokens de entrada y 300 de salida por consulta. Precio: Gemini 3.5 Flash-Lite, US$ 0,30 de entrada y US$ 2,50 de salida por millón de tokens (con Gemini 3.8 Flash, US$ 0,75 y US$ 3,75, tarifa promocional hasta el 31/12/2026); tarifa Standard, documentación oficial de Google consultada por el equipo el 26/10/2026. Dólar: $1.572 (oficial, venta Banco Nación, 26/10/2026, dato del equipo). |
| Avisos | $0 | Estimación | `wa.me` y `mailto:` los envía una persona; sin automatización. |
| Costos fijos por mes | Hoy no nos costó: $0. Cálculo a escala: pendiente | Observado (desembolso) / pendiente (escala) | El prototipo usa planes gratuitos; falta averiguar cuánto cobran la base de datos y la publicación al superar la capa gratuita. |
| Inversión inicial | 10 h × $1.956 = $19.560 | Estimación de horas × referencia (piso) | Trabajo propio de construcción del MVP, no pagado: no fue un desembolso. |

**Volumen:** 100 casos por mes = 500 pedidos (supuesto del equipo) × 20% de referencia. La tasa de devolución del e-commerce ronda el 20% (SaleCycle/Red Stag; Deloitte para Latinoamérica: 20% a 40% en temporada alta). No hay dato publicado de casos por PyME.

## Resultado y escenario

- **Contribución por marca por mes** = ingreso − soporte − IA.
- **Base (3 h):** 25.000 − 5.868 − (566 a 1.069) ≈ **$18.100 a $18.600**.
- **Exigente (6 h):** 25.000 − 11.736 − (566 a 1.069) ≈ **$12.200 a $12.700**. Solo cambian las horas.
- **Qué significa:** cada marca Pro aportaría esa cifra para cubrir fijos y luego ganancias. **No es ganancia ni prueba que una marca pague;** faltan costos fijos e inversión.

## Primeros clientes

- **Canal:** contacto directo con marcas chicas (Instagram/WhatsApp) y comunidades de emprendedores de e-commerce.
- **Costo y esfuerzo:** sin gasto en dinero; 1 h por día (5 h por semana). A $1.956 por hora, unos $9.780 por semana (referencia, no desembolso).
- **CAC / repago:** no calculables (sin clientes pagadores). Se registran marcas contactadas, respuestas, interesadas y dispuestas a pagar.

## Supuesto por comprobar

- **Supuesto:** una PyME de indumentaria online pagaría $25.000 por mes por el plan Pro.
- **Prueba:** entrevistas de precio con 5 marcas (M1 a M5). Se registran tamaño, casos por mes que declaran, si pagan algo similar, el precio que nombran **antes** de que se mencione $25.000 y quién decide. No demuestra pago efectivo.
- **Criterio previo:** éxito si al menos 3 de 5 nombran por su cuenta un precio igual o mayor a $25.000; fracaso si menos de 2 de 5; con 2 de 5, inconcluso y se hacen más entrevistas.
- **Decisión según el resultado:** éxito → piloto con compromiso previo; fracaso → recalcular con el precio que nombraron y revisar quién financia; inconcluso → más entrevistas.
- **Responsable y fecha:** las 4 integrantes del equipo, durante la semana del 26/10 al 01/11/2026.

## Fuentes

- Salario mínimo: https://www.iprofesional.com/economia/466336-salario-minimo-cuanto-se-cobra-en-octubre-y-como-aumenta-hasta-abril-2027.amp
- Tasa de devolución: https://www.a24.com/economia/de-la-tentacion-al-arrepentimiento-la-tasa-devolucion-productos-comercio-electronico-alcanza-el-20-n1240522 · https://www.innovaciondigital360.com/pago-electronico/como-impactan-los-cambios-y-devoluciones-en-ecommerce-en-la-satisfaccion-del-cliente-y-la-logistica
- Motivos de devolución (CACE): https://www.conclusion.com.ar/?p=1241597
- Dólar: oficial, venta Banco Nación, 26/10/2026 (dato del equipo).
- Planes de referencia: https://www.tiendanube.com/blog/tiendanube-costos/
- Precios de la API de Gemini (Google, tarifa Standard, consultados el 26/10/2026): https://ai.google.dev/gemini-api/docs/pricing
