\# DLP Exception Governance Agent



Agente creado en Microsoft Copilot Studio para ayudar a revisar excepciones de DLP y correlacionarlas con alertas generadas por reglas de DLP.



El objetivo del MVP es facilitar la revisión de excepciones, identificar actividad reciente asociada y ayudar a priorizar qué casos deben revisarse, renovarse, retirarse o escalarse.



\## Objetivo del proyecto



El agente permite analizar un inventario de excepciones DLP y compararlo con un export de alertas DLP para responder preguntas como:



\* Qué excepciones están activas.

\* Qué excepciones han caducado.

\* Qué excepciones tienen alertas recientes.

\* Qué excepciones activas no parecen estar siendo utilizadas.

\* Qué excepciones deberían revisarse primero.

\* Qué acción se recomienda para cada caso.



\## Fuentes de datos del MVP



El MVP utiliza dos ficheros Excel sintéticos:



```text

data/DLP\_Excepciones\_MVP\_ES.xlsx

data/DLP\_Alertas\_MVP\_ES.xlsx

```



El primer fichero representa el inventario de excepciones DLP.



El segundo fichero representa un export de alertas generadas por reglas de DLP.



La correlación principal se realiza cruzando:



```text

Solicitante = Usuario

DirectivaDLP = Directiva

Sucedido dentro de los últimos 30 días

```



El resultado principal que debe completar o explicar el agente es:



```text

Alertas30Dias

```



\## Capacidades principales



El agente está diseñado para:



\* Consultar excepciones DLP.

\* Revisar su estado y fecha de caducidad.

\* Buscar alertas relacionadas en el export DLP.

\* Calcular actividad reciente en los últimos 30 días.

\* Identificar excepciones sin uso reciente.

\* Detectar excepciones caducadas con actividad.

\* Recomendar acciones de revisión, renovación, retirada o escalado.

\* Generar resúmenes ejecutivos para equipos de seguridad o gobierno.



\## Estructura del repositorio



```text

dlp-exception-governance-agent/

│

├── README.md

├── PROJECT\_OVERVIEW.md

├── SETUP\_GUIDE.md

├── DEMO\_GUIDE.md

├── ROADMAP.md

│

├── data/

│   ├── DLP\_Excepciones\_MVP\_ES.xlsx

│   └── DLP\_Alertas\_MVP\_ES.xlsx

│

├── copilot-studio/

│   ├── agent-instructions.md

│   └── test-prompts.md

│

└── docs/

&#x20;   ├── data-model.md

&#x20;   ├── correlation-logic.md

&#x20;   └── use-cases.md

```



\## Alcance del MVP



Incluido en el MVP:



\* Dataset sintético de excepciones DLP.

\* Dataset sintético de alertas DLP.

\* Excepciones asociadas únicamente a usuarios.

\* Correlación por usuario, directiva DLP y fecha.

\* Cálculo de alertas en los últimos 30 días.

\* Recomendaciones básicas de gobierno.



Fuera del MVP:



\* Conexión directa con Microsoft Purview.

\* Uso de APIs reales.

\* Modelo en Dataverse.

\* Arquitectura multiagente.

\* Automatización completa del ciclo de vida de excepciones.

\* Acciones de remediación automáticas.



\## Uso esperado



Este proyecto está pensado como una demo funcional para un hackathon, pero con una estructura que permita evolucionarlo posteriormente hacia una solución más completa de gobierno de excepciones DLP.



\## Aviso



Los datos incluidos en el repositorio son sintéticos y no deben contener información real de usuarios, clientes, documentos sensibles o entornos productivos.



