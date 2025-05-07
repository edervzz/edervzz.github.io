# Lineamientos de Integración

Se describe a nivel general cuales son las capacidades habilitadas dentro de ecosistema de integración de Compartamos Banco.

## 1. Conectividad y Comunicación [#](/conectividad-comunicación.md)

- Protocolos de integración: REST, GRAPHQL, SOAP, gRPC, WebSockets, Near Real Time, Streaming
- Estrategia de caché

## 2. Seguridad y Control de Acceso [#](/seguridad-acceso.md)

- Autenticación: Uso de OAuth 2.0, JWT o API Keys según el caso.
- Autorización: Implementación de RBAC o ABAC para control granular.
- Protección de datos sensibles: transporte seguro de datos

## 2. Procesos y Orquestación

- Flujo de datos: Coreografía
- Modelo de comunicación: ASYNC / SYNC
- Gestión de errores: Código de error, Sincronización de estados

## 3. Modelos de Datos y Transformaciones

- Compatibilidad de esquemas: logs, payloads, errores, catálogos
- Conversión y normalización: agregación, transformación

## 4. Monitoreo y Observabilidad

- Logs y trazabilidad: eventos críticos
- Alertas y métricas: detección de anomalías
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
