# Propuesta de Lineamientos de Autenticación

## Objetivo

Definir un marco de autenticación alineado con estándares modernos y buenas prácticas, garantizando seguridad y la escalabilidad en el acceso para **colaboradores, clientes, sistemas internos y sistemas externos**.

### Actores y Métodos de Autenticación

| Actor                  | OAuth 2.0                            | JWT   | API Key                                                 |
| ---------------------- | ------------------------------------ | ----- | ------------------------------------------------------- |
| Colaboradores internos | ✅ Sí + OpenID Connect               | ✅ Sí | ❌ No                                                   |
| Clientes               | ✅ Sí + PKCE para apps móviles y web | ✅ Sí | ❌ No                                                   |
| Sistemas internos      | ✅ Sí + Client Credentials Flow      | ✅ Sí | ✅ Sí (Solo para comunicación entre servicios internos) |
| Sistemas externos      | ✅ Sí + scopes y restricciones IP    | ✅ Sí | ✅ Sí (Si es necesario para acceso limitado)            |

## Políticas de Expiración

### Tokens de Acceso

- **Colaboradores internos**: Expiración **15 minutos - 1 hora** y uso de **Refresh Tokens**.
- **Clientes**: Expiración **1 - 24 horas**, dependiendo del tipo de aplicación.
- **Sistemas internos y externos**: Expiración **1 hora - 7 días**, controlado por políticas de rotación.

### Refresh Tokens

- **Colaboradores internos:** Validez de **7 días**, con renovación automática.
- **Clientes:** Validez de **30 días**, con revocación en caso de inactividad.
- **Sistemas internos y externos:** No se recomienda Refresh Tokens, en su lugar, rotación de **API Keys o Client Credentials**.

### API Keys

- **Duración máxima recomendada:** **90 días**, con monitoreo y rotación periódica.
- **Restricciones:** Uso solo para **sistemas internos y externos**, nunca para autenticación de usuarios.

## Estrategia de Implementación

1. **Validación con el equipo de seguridad** para ajustar expiraciones y rotaciones.
2. **Pruebas de seguridad y estrés** en autenticación bajo carga alta.
3. **Monitoreo y alertas** para detectar uso indebido de credenciales.
4. **Integración con herramientas de auditoría** (ej. AWS CloudTrail, Datadog).
5. **Comunicación a equipos** sobre cambios en autenticación y políticas de expiración.
