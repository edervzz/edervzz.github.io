[Lineamientos de Integración](../../index.md#lineamientos-de-integración) / [1. Conectividad y Comunicación](../../index.md#1-conectividad-y-comunicación) / Protocolos de integración

# Protocolos de integración

## Selección del protocolo adecuado

| Protocolo  | Uso                                                    |   Formato    | R      |
| ---------- | ------------------------------------------------------ | :----------: | ------ |
| REST       | Ideal para web APIs, ampliamente adoptado (estandar)   |     JSON     | link   |
| gRPC       | Óptimo para comunicación entre microservicios          |   PROTOBUF   | Roman  |
| SOAP       | Compatibilidad en sistemas heredados                   |     XML      | Eder   |
| Mensajería | Para eventos asincríonicos y procesamiento distribuido | Cloud Events | Rafa   |
| ISO8583    | Transacciones bancarias, TPV, cajeros                  |    UTF-8     | -      |
| GraphQL    | Flexibilidad en consulta de datos y enfocado a móvil   |     JSON     | -      |
| WebSocket  | Comunicación en tiempo real                            |     JSON     | -      |
| RFC        | Óptimo para Comunicación entre sistemas SAP            |    UTF-8     | Eder✅ |
