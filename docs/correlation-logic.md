# Correlation Logic

## Objetivo

Correlacionar el inventario de excepciones DLP con el export de alertas DLP para saber si una excepción tiene actividad real reciente.

---

## Datasets usados

| Dataset                       | Uso                       |
| ----------------------------- | ------------------------- |
| `DLP_Excepciones_MVP_ES.xlsx` | Inventario de excepciones |
| `DLP_Alertas_MVP_ES.xlsx`     | Export de alertas DLP     |

---

## Regla principal de correlación

Una alerta corresponde a una excepción cuando coinciden:

| Excepciones    | Alertas     |
| -------------- | ----------- |
| `Solicitante`  | `Usuario`   |
| `DirectivaDLP` | `Directiva` |

```text
Solicitante = Usuario
AND DirectivaDLP = Directiva
```

---

## Cálculo de `Alertas30Dias`

El agente debe contar las alertas que cumplan:

```text
Usuario = Solicitante
AND Directiva = DirectivaDLP
AND Sucedido >= Today - 30 days
```

Resultado:

```text
Alertas30Dias = número de alertas encontradas
```

---

## Cálculo de `FechaUltimaActividad`

El agente debe tomar la fecha más reciente entre las alertas relacionadas:

```text
FechaUltimaActividad = MAX(Sucedido)
```

---

## Valores de canal

`Canal` en el Excel de excepciones debe usar los mismos valores que `Ubicación` en el export de alertas:

```text
Endpoint devices
Exchange
OneDrive
SharePoint
Teams
```

En el MVP, `Canal` es contexto. La correlación principal se hace por:

```text
Solicitante + DirectivaDLP + Fecha
```

---

## Reglas de exclusión

El agente no debe contar una alerta si:

* El usuario no coincide.
* La directiva DLP no coincide.
* La alerta tiene más de 30 días.
* La directiva no corresponde a una política de excepción `EXCL`.
* La excepción no está lista para evaluación.

---

## Resultado esperado

El agente debe completar o actualizar:

| Campo                  | Resultado                             |
| ---------------------- | ------------------------------------- |
| `Alertas30Dias`        | Nº de alertas relacionadas en 30 días |
| `FechaUltimaActividad` | Última fecha de alerta relacionada    |
| `PuntuacionRiesgo`     | Scoring calculado                     |
| `NivelRiesgo`          | Bajo / Medio / Alto / Crítico         |
| `AccionRecomendada`    | Renovar / Revisar / Retirar / Escalar |
