# 🛡️ DLP Exception Governance Agent

Agente creado en **Microsoft Copilot Studio** para ayudar a revisar excepciones de DLP y correlacionarlas con alertas generadas por reglas de DLP.

> El objetivo del MVP es facilitar la revisión de excepciones, identificar actividad reciente asociada y priorizar qué casos deben revisarse, renovarse, retirarse o escalarse.

---

## 🎯 Objetivo

El agente permite analizar un inventario de excepciones DLP y compararlo con un export de alertas DLP para responder preguntas como:

| Pregunta                                      | Valor                      |
| --------------------------------------------- | -------------------------- |
| ¿Qué excepciones están activas?               | Visibilidad del inventario |
| ¿Qué excepciones han caducado?                | Control de gobierno        |
| ¿Qué excepciones tienen alertas recientes?    | Evidencia de uso           |
| ¿Qué excepciones activas no tienen actividad? | Posible retirada           |
| ¿Qué excepciones deben revisarse primero?     | Priorización de riesgo     |

---

## 📂 Fuentes de datos del MVP

El MVP utiliza dos ficheros Excel sintéticos:

```text
data/DLP_Excepciones_MVP_ES.xlsx
data/DLP_Alertas_MVP_ES.xlsx
```

| Dataset                       | Descripción                                |
| ----------------------------- | ------------------------------------------ |
| `DLP_Excepciones_MVP_ES.xlsx` | Inventario de excepciones DLP              |
| `DLP_Alertas_MVP_ES.xlsx`     | Export de alertas generadas por reglas DLP |

---

## 🔗 Lógica principal

La correlación entre ambos datasets se basa en:

```text
Solicitante = Usuario
DirectivaDLP = Directiva
Sucedido dentro de los últimos 30 días
```

El resultado principal es el cálculo de:

```text
Alertas30Dias
```

---

## ✅ Capacidades principales

El agente está diseñado para:

* Consultar excepciones DLP.
* Revisar estado y fecha de caducidad.
* Buscar alertas relacionadas en el export DLP.
* Calcular actividad reciente en los últimos 30 días.
* Detectar excepciones activas sin uso reciente.
* Identificar excepciones caducadas con actividad.
* Recomendar acciones de revisión, renovación, retirada o escalado.
* Generar resúmenes ejecutivos para equipos de seguridad o gobierno.

---

## 🧱 Estructura del repositorio

```text
dlp-exception-governance-agent/
│
├── README.md
├── PROJECT_OVERVIEW.md
├── SETUP_GUIDE.md
├── DEMO_GUIDE.md
├── ROADMAP.md
│
├── data/
│   ├── DLP_Excepciones_MVP_ES.xlsx
│   └── DLP_Alertas_MVP_ES.xlsx
│
├── copilot-studio/
│   ├── agent-instructions.md
│   └── test-prompts.md
│
└── docs/
    ├── data-model.md
    ├── correlation-logic.md
    └── use-cases.md
```

---

## 📌 Alcance del MVP

### Incluido

| Incluido en el MVP                             |
| ---------------------------------------------- |
| Dataset sintético de excepciones DLP           |
| Dataset sintético de alertas DLP               |
| Excepciones asociadas a usuarios               |
| Correlación por usuario, directiva DLP y fecha |
| Cálculo de alertas en los últimos 30 días      |
| Recomendaciones básicas de gobierno            |

### Fuera de alcance

| No incluido en el MVP                     |
| ----------------------------------------- |
| Conexión directa con Microsoft Purview    |
| Uso de APIs reales                        |
| Modelo en Dataverse                       |
| Arquitectura multiagente                  |
| Automatización completa del ciclo de vida |
| Remediación automática                    |

---

## 🚀 Uso esperado

Este proyecto está pensado como una **demo funcional para un hackathon**, manteniendo una estructura sencilla pero escalable.

La idea es demostrar cómo un agente puede ayudar a gobernar excepciones DLP combinando:

```text
Inventario de excepciones
+
Actividad real de alertas
+
Recomendaciones accionables
```

---

## ⚠️ Aviso

Los datos incluidos en el repositorio son **sintéticos**.

No deben incluirse datos reales de usuarios, clientes, documentos sensibles o entornos productivos.




