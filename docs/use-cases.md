# Use Cases

## Objetivo

El agente ayuda a revisar excepciones DLP usando el inventario de excepciones y la actividad real del export de alertas.

---

## Casos de uso del MVP

| Caso de uso                                  | Qué hace el agente                                  |
| -------------------------------------------- | --------------------------------------------------- |
| Revisar excepciones activas                  | Lista excepciones vigentes y su estado              |
| Calcular actividad reciente                  | Completa `Alertas30Dias`                            |
| Detectar excepciones sin uso                 | Encuentra excepciones activas sin alertas recientes |
| Detectar excepciones caducadas con actividad | Identifica riesgo no gestionado                     |
| Priorizar revisión                           | Ordena excepciones por riesgo                       |
| Recomendar acciones                          | Propone renovar, revisar, retirar o escalar         |
| Generar resumen ejecutivo                    | Resume estado, riesgos y acciones                   |

---

## Prompts de prueba

### Revisar excepciones activas

```text
Muéstrame las excepciones activas y resume su estado.
```

### Calcular alertas recientes

```text
Calcula las alertas de los últimos 30 días para cada excepción.
```

### Detectar excepciones sin uso

```text
¿Qué excepciones activas no tienen actividad en los últimos 30 días?
```

### Detectar caducadas con actividad

```text
¿Qué excepciones caducadas siguen generando alertas?
```

### Priorizar revisión

```text
Prioriza las excepciones que deberían revisarse primero.
```

### Recomendar acciones

```text
Recomienda una acción para cada excepción activa.
```

### Resumen ejecutivo

```text
Genera un resumen ejecutivo del estado de las excepciones DLP.
```

---

## Acciones recomendadas

| Acción                 | Cuándo aplica                                 |
| ---------------------- | --------------------------------------------- |
| `Renovar`              | Excepción activa, justificada y con actividad |
| `Revisar`              | Actividad dudosa o necesita validación        |
| `Retirar`              | Excepción activa sin actividad reciente       |
| `Escalar`              | Excepción caducada o riesgo alto              |
| `Sin acción inmediata` | Excepción controlada y bajo riesgo            |

---

## Fuera de alcance del MVP

* Conexión directa con Microsoft Purview.
* Remediación automática.
* Dataverse.
* Power BI.
* SIEM o ticketing.
* Arquitectura multiagente.
