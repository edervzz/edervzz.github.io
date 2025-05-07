# 4. Monitoreo y Observabilidad

## Logs y trazabilidad

### Eventos críticos

Capturar las los eventos esenciales que impactan la operación e integración.

**Solicitudes y Respuestas de APIs**: incluir detalles de los tiempos de procesamiento (métricas), mensajes relevantes (logs) códigos de respuesta y payloads que sea relevantes (excluyendo datos sensibles). Incluir identificadores de correlación entre sistemas para rastreo de operaciones E2E.

- Todos los servicios deben ser instrumentados, sanitizados y aquellos que realicen mutaciones deben incluir payloads.
- Generar registro detallado de las excepciones y fallas del sistema, incluyendo códigos de error que puedan ser utilizados por el equipo técnico para su identificación.
- Las operaciones de mutación deben usar un ID de Correlación para ligar logs entre los sistemas consumidor y proveedor.
- Dentro de los flujos de negocio, incluir detalle del evento de aprobación o rechazo

### Estrategia de logs y definición de niveles de severidad

Los logs deben ser estructurados en formato JSON para su fácil análisis, centralizados en herramientas como Datadog y hacer uso de niveles de severidad.

- INFO. Información importante de la operación, hitos o marcas.
- WARN. Comportamiento inesperado que puede escalar si no es atendido. (carga de CPU, disco, latencia)
- ERROR. Fallo en una operación pero no causa una falla total. (validaciones de negocio, error de conexión de DB)
- CRITICAL. Falla grave en el sistema que impide su operación. (caída de servicios clave, perdida total con DB, afecta a todos los usuarios)
