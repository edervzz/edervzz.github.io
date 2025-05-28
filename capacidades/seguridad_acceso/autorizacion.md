[Lineamientos de Integración](../../index.md#lineamientos-de-integración) / [2. Seguridad y Control de Acceso](../../index.md#2-seguridad-y-control-de-acceso) / Lineamientos de Autorización

# Lineamientos de Autorización

**Autorización**: _Proceso mediante el cual se determinan los **permisos y accesos** que un usuario o sistema tienen sobre un determinado recurso._

## Objetivo

Definir un marco para la gestión de permisos y accesos dentro de los sistemas, garantizando que los **colaboradores, clientes, sistemas internos y externos** tenga los privilegios adecuados a los recursos solicitados según necesidad la operativa.

### Principios Fundamentales

- **Integración con Sailpoint**: todas las aplicaciones que sean capaces de integración deben delegar la gestión de roles y accesos a través de Sailpoint.

- **Autorización autónoma**: aquellas aplicaciones con no sean capaces de integrarse deben contar con un mecanismo o sistema propio que cumpla con estandares de seguridad y trazabilidad.

- **Principio de mínimo privilegio**: se debe asignar únicamente los accesos necesario para evitar mal uso de los recursos.

- **Auditoria**: todas las aplicaciones tanto propias como externas, deben registrar los eventos de acceso para su análisis y cumplimiento.

### Control y Evaluación

- **Revisión mensual/trimestral/semestral de accesos**, asegurando que roles y permisos sean los adecuados.
- **Trazabilidad de accesos**, aplicaciones sin integración deben proveer logs de autorización para analisis y cumplimiento.

### Métodos de Autorización

| Método | Uso                                                                                          |
| ------ | -------------------------------------------------------------------------------------------- |
| RBAC   | Permisos asignador según el rol del usuario, ideal para entornos empresariales.              |
| ABAC   | Basado en atributos, útil en escenarios dinámicos donde los accesos dependen de condiciones. |
