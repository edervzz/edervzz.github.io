# 1. Conectividad y Comunicación

## Protocolos de integración

### Selección del protocolo adecuado

| Protocolo  | Uso                                                    |   Formato    |
| ---------- | ------------------------------------------------------ | :----------: | ------ |
| REST       | Ideal para web APIs, ampliamente adoptado (estandar)   |     JSON     | link   |
| gRPC       | Óptimo para comunicación entre microservicios          |   PROTOBUF   | Roman  |
| SOAP       | Compatibilidad en sistemas heredados                   |     XML      | Isaac  |
| Mensajería | Para eventos asincríonicos y procesamiento distribuido | Cloud Events | Rafa   |
| ISO8583    | Transacciones bancarias, TPV, cajeros                  |    UTF-8     | -      |
| GraphQL    | Flexibilidad en consulta de datos y enfocado a móvil   |     JSON     | -      |
| WebSocket  | Comunicación en tiempo real                            |     JSON     | -      |
| RFC        | Óptimo para Comunicación entre sistemas SAP            |    UTF-8     | Eder✅ |

### Incorporación de caché. _Reducir la dependencia a consultas repetitivas_

La incorporación de caché depende de 3 factores a considerar:

- Frecuencia de cambios en los catálogos
  - Los datos cambian diariamente. _Time-To-Live (TTL) Fijo_
  - Los datos cambian constantemente. _Por evento Write-through Cache_
- Cantidad de consultas
  - Alta demanda. _TTL corto 30min - 1hr_
  - Baja demanda. _TTL largo / Read-through Cache / Cache LRU_
- Consistencia de datos
  - Precisa. _Write-through Cache_
  - Tolerante. _TTL medio varias horas_

| Estrategia          | Caso                                                      |
| ------------------- | --------------------------------------------------------- |
| Time-To-Live Fijo   | Actualizaciones diarias. Es tolerante. Demanda media/alta |
| Write-through Cache | Cambios constantes o información precisa                  |
| Read-through Cache  | Demanda baja e información precisa                        |
| Cache LRU           | Demanda media. Grandes volúmenes de datos                 |
