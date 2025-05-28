[Lineamientos de Integración](../../index.md#lineamientos-de-integración) / [5. Monitoreo y Observabilidad](../../index.md#5-monitoreo-y-observabilidad) / Logs y trazabilidad

# Logs y trazabilidad

**Logs**: Registro de eventos generados por aplicaciones o sistemas permitiendo el diagnostico de errores y comportamientos del software.

**Trazabilidad**: Capacidad de seguir el recorrido de una solicitud o proceso a través de uno o varios servicios, ayudando a identificar cuellos de botella y mejora del rendimiento.

## Eventos críticos

Capturar las los eventos esenciales que impactan la operación e integración.

**Solicitudes y Respuestas de APIs**: incluir detalles de los tiempos de procesamiento (métricas), mensajes relevantes (logs) códigos de respuesta y payloads que sea relevantes (excluyendo datos sensibles). Incluir identificadores de correlación entre sistemas para rastreo de operaciones E2E.

- Todos los servicios deben ser instrumentados, sanitizados y aquellos que realicen mutaciones deben incluir payloads.
- Generar registro detallado de las excepciones y fallas del sistema, incluyendo códigos de error que puedan ser utilizados por el equipo técnico para su identificación.
- Las operaciones de mutación deben usar un ID de Correlación para ligar logs entre los sistemas consumidor y proveedor.
- Dentro de los flujos de negocio, incluir detalle del evento de aprobación o rechazo

### Estrategia de logs y definición de niveles de severidad. _CloudWatch_

Los logs deben ser estructurados en formato JSON para su fácil análisis, centralizados en herramientas como Datadog y hacer uso de niveles de severidad.

- INFO. Información importante de la operación, hitos o marcas.
- WARN. Comportamiento inesperado que puede escalar si no es atendido. (carga de CPU, disco, latencia)
- ERROR. Fallo en una operación pero no causa una falla total. (validaciones de negocio, error de conexión de DB)
- CRITICAL. Falla grave en el sistema que impide su operación. (caída de servicios clave, perdida total con DB, afecta a todos los usuarios)

```json
{
  /* Ejemplo de log */
  "timestamp": "2025-05-07T18:00:00Z",
  "level": "ERROR",
  "message": "Fallo en la comunicación con el servicio de autenticación",
  "service": "banca-movil",
  "request_id": "b2a3f123-4567-890d-abc1-23456789efgh",
  "correlation_id": "a1b2c3d4-5678-9101-1121-314151617181",
  "user_id": "30054",
  "extra_data": {
    "endpoint": "/auth/login",
    "http_status": 503,
    "retry_attempts": 2
  }
}
```

### Gestión de Correlation ID

El Correlation ID permite rastrear una transacción entre distintos sistemas. Consideraciones clave:

- **Generar** UUID v4 al inicio de cada solicitud.
- Cada servicio debe **propagar** el mismo ID en llamadas internas.
- El Correlation ID debe **registrarse** en logs y trazas.
- Ejemplo de uso en API:
  - Banca Móvil envía solicitud con Correlation ID.
  - API lo mantiene en la respuesta y lo transmite en llamadas internas.
  - En caso de que un servicio no reciba un ID, genera uno nuevo y lo propaga.

### Alertas y metricas. _CloudWatch Alarms, X-Ray, Logs Insights, Grafana_

- Thresholds definidos por servicio

  - Normal: < 300 ms
  - Advertencia: 300-500 ms
  - Crítico: > 500 ms

- Errores recurrentes

  - Advertencia: > 2% de respuestas 4XX en 5 min
  - Crítico: > 5% de respuestas 5XX en 5 min

- Consumo de CPU y memoria

  - Advertencia: CPU/Memoria > 70%
  - Crítico: CPU/Memoria > 90%

- Estrategioa de notificaciones
  - Advertencias: Slack, Team
  - Críticos: SMS, Email
  - Visualización: Dashboard (Amazon Managed Grafana)
