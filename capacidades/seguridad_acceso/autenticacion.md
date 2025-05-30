[Lineamientos de Integración](../../index.md#lineamientos-de-integración) / [2. Seguridad y Control de Acceso](../../index.md#2-seguridad-y-control-de-acceso) / Lineamientos de Autenticación

# Lineamientos de Autenticación

**Autenticación**: _Proceso de **verificar la identidad** de un usuario, aplicación o dispositivo antes de permitirle acceder a un sistema o servicio, asegurando que la entidad que intenta ingresar es quien dice ser._

## Objetivo

Definir un marco de autenticación alineado con estándares modernos y buenas prácticas, garantizando seguridad y la escalabilidad en el acceso para **colaboradores, clientes, sistemas internos y sistemas externos**.

### Métodos de Autenticación

| Método    | Uso                                                                                                                  |
| --------- | -------------------------------------------------------------------------------------------------------------------- |
| OAuth 2.0 | Aplicaciones donde los usuarios necesitan conectarse a sistemas sin exponer credenciales.                            |
| JWT       | Autenticación de APIs para sesiones sin estado, validación de usuarios rápida.                                       |
| API Keys  | Autorización entre servidores donde no hay intervención directa de usuarios finales. Considerar restricciones de IP. |

### Actores vs Métodos de Autenticación

| Actor                  | OAuth 2.0                           | JWT  | API Key                                                |
| ---------------------- | ----------------------------------- | ---- | ------------------------------------------------------ |
| Colaboradores internos | ✅Sí + OpenID Connect               | ✅Sí | ❌ No                                                  |
| Clientes               | ✅Sí + PKCE para apps móviles y web | ✅Sí | ❌ No                                                  |
| Sistemas internos      | ✅Sí + Client Credentials Flow      | ✅Sí | ✅Sí (Solo para comunicación entre servicios internos) |
| Sistemas externos      | ✅Sí + scopes y restricciones IP    | ✅Sí | ✅Sí (Si es necesario para acceso limitado)            |

## Políticas de Expiración

Defincir los tiempos de expiración estandar de tokens, según sea el usuario: **colaboradores, clientes, sistemas internos y sistemas externos**.

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

### Estrategia de Implementación

1. **Validación con el equipo de seguridad** para ajustar expiraciones y rotaciones.
2. **Pruebas de seguridad y estrés** en autenticación bajo carga alta.
3. **Monitoreo y alertas** para detectar uso indebido de credenciales.
4. **Integración con herramientas de auditoría** (ej. AWS CloudTrail, Datadog).
5. **Comunicación a equipos** sobre cambios en autenticación y políticas de expiración.

## Casos de Uso

A continuación se describen ejemplos de la aplicación de métodos de autenticación a cada actor.

### Colaboradores internos. OAuth 2.0 + OpenID Connect

- Un gerente de OS necesita acceder a herramientas del banco como es el sistema de gestión de clientes y el dashboard de métricas de ventas.

- Un desarrollador interno necesita acceso a los ambientes de desarrollo y pruebas en GCP/AWS para desplegar nuevos cambios en los servicios.

✅Con OpenID Connect realizamos una autenticación a través de un proveedor de identidad, de esta forma aseguramos que el usuario es quien dice ser, solo colaboradores autorizados accedan a información sensible.

✅Los colaboradores pueden ingresar a múltiples aplicaciones sin tener que ingresar repetidamente sus credenciales o generar tokens manuales, reduciendo el riesgo de exposición de credenciales.

✅A través de roles y permisos adecuados podemos asignar aquellos que este acorde al usuario. Dando acceso a las aplicaciones y ambientes pertinentes

---

### Clientes. OAuth 2.0 + PKCE

- Un cliente utiliza la banca móvil para consultar su saldo y realizar transferencias bancarias sin necesidad de ingresar sus credenciales cada que se accede las multiples operaciones.

- Un usuario quien acaba de abrir su cuenta Compartamos desea vincular su dispositivo para realizar sus operaciones en línea.

✅PKCE evita el robo de códigos de autorización en aplicaciones móviles o SPA's. PKCE permite a los usuarios autenticarse dentro de las Apps sin depender de redirecciones a enlaces externos.

✅La App no necesita resguardar la credenciales ya que el proceso de autenticación usa códigos dinámicos.

✅Al minimizar el uso de acceso con credenciales también se elimina la exposición de las mismas.

---

### Sistemas internos. OAuth 2.0 + Client Credential Flow

- Un sistema de procesamiento de pagos necesita consultar el servicio de consulta de cuentas bancarias para validar la existencia de la cuenta y su estado antes de procesar una transacción.

- Los sistemas de auditoría interna acceden periodicamente a los logs dentro del core bancario para la generación de reportes.

✅Dado que se trata de una comunicación entre sistemas, Client Credential Flow permite el intercambio seguro sin la participación de un usuario.

✅Los servicios puede solicitar tokens según se necesiten sin comprometer la seguridad o fricción con usuarios.

✅En caso de requerir tratar con datos sensibles, podemos definir scopes para los servicios autorizados.

---

### Sistemas internos. OAuth 2.0 + Client Credential Flow + Scopes + Restricciones IP

- Un proveedor de telefonía requiere conectarse a una API de core para generar cobros a clientes por el uso de servicios.

- Un servicio de detección de fraudes solicita acceso a datos bancarios limitados para evaluar patrones sospechosos en las transacciones.

✅El uso de scopes puede limitar a los sistemas externos a consultas y operaciones especificas.

✅Solo solicitudes desde direcciones IP verificadas pueden acceder a la API, reduciendo riesgos de ataques.

✅Al usar Client Credencia Flow se garantiza la interacción entre sistemas sin necesidad de un usuario.

```

```
