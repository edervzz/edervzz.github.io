# Lineamientos de Integración

Se describe a nivel general cuales son las capacidades habilitadas dentro de ecosistema de integración de Compartamos Banco.

## 1. Conectividad y Comunicación

- [Protocolos de integración](/capacidades/conectividad_comunicacion/protocolos.md) : REST, GRAPHQL, SOAP, gRPC, WebSockets, Near Real Time, Streaming
- [Estrategia de caché](/capacidades/conectividad_comunicacion/cache.md): Cadencia, Consistencia.

## 2. Seguridad y Control de Acceso

- [Autenticación](/capacidades/seguridad_acceso/autenticacion.md): Uso de OAuth 2.0, JWT o API Keys según el caso.
- [Autorización](/capacidades/seguridad_acceso/autorizacion.md) : Implementación de RBAC o ABAC para control granular.
- Protección de datos sensibles: transporte seguro de datos

## 3. Procesos y Orquestación

- Flujo de datos: Coreografía
- Modelo de comunicación: ASYNC / SYNC
- Gestión de errores: Código de error, Sincronización de estados

## 4. Modelos de Datos y Transformaciones

- Compatibilidad de esquemas: logs, payloads, errores, catálogos
- Conversión y normalización: agregación, transformación

## 5. Monitoreo y Observabilidad

- [Logs y trazabilidad](/capacidades/monitore_observabilidad/logs_trazabilidad.md): eventos críticos
- [Alertas y métricas](/capacidades/monitore_observabilidad/alertas_metricas.md): detección de anomalías
- Auditoría de transacciones: Identificadores de correlación entre sistemas

## 6. Operación y Mantenimiento

- Versionamiento de APIs: manejo y difusión de los cambios de versiones al equipo TI
- Automatización de pruebas: Pruebas unitarias, integración y E2E, reducción de costos y tiempo

# 7. Modelo de Despliegue y Ambientes

- Ambientes: diferenciación entre desarrollo, prueba y producción
- Estrategias de despliegue: Blue-Green Deployment, Canary
- Infraestructura y compatibilidad: on-premise, en la nube o híbrida
- Gestión de configuración: variables de entorno y credenciales por ambiente
- Automatización de infraestructura: Harness, CloudFormation, Terraform

## 8. Analítica (Riesgos, métricas, consumo performance)

- ?
