# Architecture Decision Records (ADRs)

Los ADRs crean una base de conocimiento que preservan el conocimiento arquitectónico, registrando el contexto del razonamiento detrás de las decisiones esenciales de diseño.

Un ADR es un documento corto que captura una única e importante decisión sobre la arquitectura de un sistema de software. En la práctica, puede ser tan simple como un markdown o una entrada en la documentación.

Los ADR deben registrar decisiones realmente relevantes de elecciones arquitectónicas que afectan la estructura del sistema, características no funcionales, dependencias, interfaces o técnicas de construcción.

Las principales beneficios de documentar decisiones de arquitectura. - Retención del conocimiento, porque no importara la rotación del equipo, el proyecto seguirá ahí. Los ADRs preservan el razonamiento original detrás de una decisión clave. Meses después alguien puede leer los ADRs y entender nuestro pensar. - Mejor colaboración, los ADRs impulsan al equipo a discutir y a estar de acuerdo con decisiones importantes, en lugar de solo tomar la opción adecuada y olvidarla, un ADR suele ser propuesto, revisado, y aceptado por el equipo. - Evolución Arquitectónica, mientras pasa el tiempo los requerimientos cambian, y algunas decisiones pudieran ser revisadas, los ADRs hacen que la evolución arquitectónica sea más manejable, al leer porque se tomaron esas decisiones y cuáles fueron los acuerdos aceptados podríamos determinar si el contexto original sigue vigente o si es momento de cambiar el curso. - Contar con el mapa completo, necesitamos los ADRs para resolver preguntas sin respuesta del código, objetivos del sistema, requerimientos no funcionales, decisiones de arquitectura y sus argumentos.

En esencia los ARDs son una capa ligera de memoria de arquitectura dentro de tu proyecto. Estos aseguran que las lecciones aprendidas y el razonamiento detrás de las elecciones de diseño no sea olvidadas con el paso del tiempo. Invertir algunas horas en escribir nutridamente un ADR puede ahorrar horas de esfuerzo innecesario en el futuro y prevenir errores costosos del pasado por falta de contexto.

```md
# Title: [Short, descriptive title]

## Status

[Proposed | Accepted | Deprecated]

## Date

YYYY-MM-DD

## Context

[Describe the problem and context. What forces are at play? What constraints exist?]

## Decision

[State the decision clearly and concisely]

## Consequences

### Positive

- [Positive outcome 1]
- [Positive outcome 2]

### Negative (Trade-off)

- [Negative consequence 1]
- [Negative consequence 2]

### Follow-ups

[Derivado de los Trade-offs, cual es el seguimiento acordado]

## Alternatives (up to 3)

[Describe other options and why they weren't chosen]

## References

[Optional: Link to relevant documents, patterns, or resources]
```
