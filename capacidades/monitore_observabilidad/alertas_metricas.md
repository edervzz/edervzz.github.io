[Lineamientos de Integración](../../index.md#lineamientos-de-integración) / [5. Monitoreo y Observabilidad](../../index.md#5-monitoreo-y-observabilidad) / Alertas y metricas

# Alertas y metricas

**Métricas**: Datos cuantificables que reflejan el estado y rendimiento del sistema. Uso de CPU, latencia de API's o número de solicitudes procesadas.

**Alertas**: Son notificaciones lanzadas cuando una métrica es superada según su umbral definido. Una API excede los 500ms en dar una respuesta.

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
