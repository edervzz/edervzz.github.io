# 2. Seguridad y Control de acceso

Uso de OAuth 2.0, JWT o API Keys según el caso.

Implementación de RBAC o ABAC para control granular.

## Autenticación

Proceso de **verificar la identidad** de un usuario o servicio antes de permitirle acceso.

_Se asegurda de que la persona o sistema que intenta ingresar es quien dice ser._

| Método    | Uso                                                                                                                  |
| --------- | -------------------------------------------------------------------------------------------------------------------- |
| OAuth 2.0 | Aplicaciones donde los usuarios necesitan conectarse a sistemas sin exponer credenciales                             |
| JWT       | Autenticación de APIs para sesiones sin estado, validación de usuarios rápida                                        |
| API Keys  | Autorización entre servidores donde no hay intervención directa de usuarios finales. Considerar restricciones de IP. |

## Autorización

Define **qué acciones puede realizar** un usuario una vez autenticado.

_Una vez verificada su identidad, el sistema establece los permisos sobre recursos._

### RBAC (Role-Based Access Control): para aplicaciones con estructuras claras y permisos predefinidos

💡*Baja flexibilidad, fácil administración, escalabilidad limitada*

- Definición de Roles
- Asignación de Permisos a Rol
- Asociación de Roles a Usuarios

Ej. Roles Admin, Manager, User para el manejo del sistema. Nuevos equipos podrian implicar nuevos roles.

### ABAC (Attribute-Based Access Control): para aplicaciones dinámicas con reglas más precisas y contexto variable.

💡*Alta flexibilidad, administración compleja, alta escalabilidad*

- Definir atributros relevantes
- Creación de reglas basadas en atributos
- Implementar evaluación de politicas (OPA)

Ej. Acceso al sistema solo si se trabaja en horario laboral y desde una IP dentro de la empresa.

## Datos Sensibles

Aplicar estrategias de seguridad y control para proteger la integridad y confiabilidad de la informacón.

- Clasificación de datos: personal, financiero, secreto.
- Políticas de Acceso por nivel: público, interno, confidencia, restringido.
- Aplicación de RBAC, ABAC o ambos.
- Desactivar logs con información sensible: definición de filtros que excluyan datos sensibles (log masking).
- Cifrado de datos en reposo y transito.
