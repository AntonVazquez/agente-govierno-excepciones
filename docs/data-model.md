# Data Model

## Datasets

| Fichero                       | Descripción                   |
| ----------------------------- | ----------------------------- |
| `DLP_Excepciones_MVP_ES.xlsx` | Inventario de excepciones DLP |
| `DLP_Alertas_MVP_ES.xlsx`     | Export de alertas DLP         |

---

## DLP Exceptions Dataset

Fuente principal para el gobierno de excepciones.

| Columna                       | Uso                                   |
| ----------------------------- | ------------------------------------- |
| `IDExcepcion`                 | Identificador único                   |
| `Solicitante`                 | Usuario que solicita la excepción     |
| `Departamento`                | Área del solicitante                  |
| `JustificacionNegocio`        | Motivo de negocio                     |
| `Canal`                       | Ubicación/canal DLP                   |
| `DirectivaDLP`                | Directiva DLP de excepción            |
| `TipoDatoSensible`            | Tipo de dato afectado                 |
| `EstadoComunicacion`          | Estado de comunicación con el usuario |
| `EstadoRespuestaFormulario`   | Estado del formulario                 |
| `Aprobador`                   | Responsable de aprobación             |
| `EstadoAprobacion`            | Estado de aprobación                  |
| `FechaCaducidad`              | Fecha de vencimiento                  |
| `EstadoExcepcion`             | Estado calculado de la excepción      |
| `Alertas30Dias`               | Alertas relacionadas en 30 días       |
| `FechaUltimaActividad`        | Última actividad DLP                  |
| `ListaParaEvaluacion`         | Indica si se puede evaluar            |
| `PuntuacionRiesgo`            | Scoring de riesgo                     |
| `NivelRiesgo`                 | Bajo / Medio / Alto / Crítico         |
| `ExplicacionRiesgo`           | Motivos del riesgo                    |
| `AccionRecomendada`           | Acción propuesta                      |
| `FechaUltimaEvaluacionRiesgo` | Fecha de evaluación                   |

---

## DLP Alerts Dataset

Fuente de actividad real generada por reglas DLP.

| Columna                                         | Uso                           |
| ----------------------------------------------- | ----------------------------- |
| `Archivo`                                       | Archivo afectado              |
| `Ubicación`                                     | Canal donde ocurrió la alerta |
| `Usuario`                                       | Usuario asociado              |
| `Sucedido`                                      | Fecha de la alerta            |
| `Tipo de información confidencial`              | Dato sensible detectado       |
| `Recuento del tipo de información confidencial` | Nº de coincidencias           |
| `Directiva`                                     | Directiva DLP                 |
| `Regla`                                         | Regla DLP                     |
| `Destinatario del correo electrónico`           | Destinatario, si aplica       |
| `Extensión de archivo`                          | Tipo de archivo               |
| `Tamaño del archivo`                            | Tamaño                        |
| `Aplicación`                                    | Aplicación implicada          |
| `Modo de cumplimiento`                          | Modo de la directiva          |
| `Dominio de destino`                            | Dominio externo, si aplica    |
| `Tipo de actividad`                             | Acción detectada              |

---

## Relación entre datasets

| Excepciones    | Alertas     |
| -------------- | ----------- |
| `Solicitante`  | `Usuario`   |
| `DirectivaDLP` | `Directiva` |

`Sucedido` se usa para calcular actividad en los últimos 30 días.

---

## Campos calculados por el agente

| Campo                         | Origen                |
| ----------------------------- | --------------------- |
| `Alertas30Dias`               | Export de alertas     |
| `FechaUltimaActividad`        | Export de alertas     |
| `PuntuacionRiesgo`            | Scoring del agente    |
| `NivelRiesgo`                 | Scoring del agente    |
| `ExplicacionRiesgo`           | Evaluación del agente |
| `AccionRecomendada`           | Evaluación del agente |
| `FechaUltimaEvaluacionRiesgo` | Fecha de análisis     |
