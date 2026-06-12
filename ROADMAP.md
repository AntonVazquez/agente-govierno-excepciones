# Roadmap

## Objetivo

Evolucionar el **DLP Exception Governance Agent** desde el MVP actual hacia una solución más automatizada, integrada y escalable para gobierno de excepciones DLP.

---

## Estado actual

| Elemento                   | Estado                              |
| -------------------------- | ----------------------------------- |
| Agente en Copilot Studio   | Creado / MVP                        |
| Inventario de excepciones  | Excel                               |
| Export de alertas DLP      | Excel                               |
| Correlación                | Solicitante + Directiva DLP + Fecha |
| Cálculo de `Alertas30Dias` | Definido                            |
| Scoring de riesgo          | Básico                              |
| Documentación inicial      | Disponible                          |
| Automatización             | Siguiente paso                      |

---

# Fase 2 · Automatización del MVP

## Objetivo

Reducir tareas manuales y permitir que el agente actualice el inventario de excepciones con información calculada desde el export de alertas DLP.

## Mejoras clave

* Crear acción para actualizar `Alertas30Dias`.
* Crear acción para actualizar `FechaUltimaActividad`.
* Crear acción para actualizar:

  * `PuntuacionRiesgo`
  * `NivelRiesgo`
  * `ExplicacionRiesgo`
  * `AccionRecomendada`
  * `FechaUltimaEvaluacionRiesgo`
* Validar que el agente no actualiza excepciones no listas para evaluación.
* Añadir prompts de validación para comprobar la correlación.
* Generar resumen ejecutivo desde el agente.

## Resultado esperado

```text
Agente capaz de analizar y actualizar el inventario de excepciones de forma asistida.
```

---

# Fase 3 · Gobierno del ciclo de vida

## Objetivo

Convertir el agente en una herramienta de seguimiento continuo de excepciones.

## Mejoras clave

* Detectar excepciones próximas a caducar.
* Enviar recordatorios al solicitante o aprobador.
* Solicitar confirmación de renovación mediante formulario.
* Registrar si la excepción debe renovarse, retirarse o revisarse.
* Escalar excepciones caducadas con actividad.
* Guardar evidencia de revisión.
* Mantener trazabilidad de decisiones.

## Resultado esperado

```text
Proceso de revisión de excepciones más controlado, repetible y trazable.
```

---

# Fase 4 · Optimización del scoring

## Objetivo

Mejorar la priorización de riesgo y hacer el análisis más defendible.

## Mejoras clave

* Ajustar pesos del scoring.
* Diferenciar criticidad por tipo de dato sensible.
* Considerar volumen de alertas.
* Considerar canal de exposición.
* Considerar caducidad y proximidad al vencimiento.
* Añadir tendencia de actividad.
* Separar riesgo operativo y riesgo de gobierno.

## Resultado esperado

```text
Priorización más precisa de las excepciones que requieren revisión.
```

---

# Fase 5 · Modelo de datos robusto

## Objetivo

Reducir la dependencia de Excel y preparar el agente para un uso más escalable.

## Mejoras clave

* Migrar el inventario a Dataverse.
* Crear entidades separadas para:

  * Excepciones
  * Alertas
  * Usuarios
  * Aprobaciones
  * Evaluaciones de riesgo
  * Acciones recomendadas
* Añadir historial de cambios.
* Mejorar control de permisos.
* Estandarizar estados y valores.

## Resultado esperado

```text
Modelo de datos más sólido, gobernado y preparado para operación recurrente.
```

---

# Fase 6 · Integración con Microsoft Purview

## Objetivo

Eliminar la carga manual de exports y conectar el agente con fuentes reales de actividad DLP.

## Mejoras clave

* Explorar conexión con Microsoft Purview.
* Automatizar la ingesta de alertas DLP.
* Normalizar alertas por usuario, directiva, canal y fecha.
* Mantener histórico de actividad.
* Comparar actividad antes y después de aprobar una excepción.
* Detectar políticas de excepción con uso anómalo.

## Resultado esperado

```text
Agente alimentado por actividad DLP real sin depender de exports manuales.
```

---

# Fase 7 · Reporting y visibilidad

## Objetivo

Facilitar seguimiento ejecutivo y revisión periódica.

## Mejoras clave

* Crear informes periódicos.
* Mostrar excepciones activas, caducadas y próximas a caducar.
* Mostrar excepciones sin actividad.
* Mostrar excepciones con mayor volumen de alertas.
* Mostrar evolución mensual.
* Añadir métricas de gobierno.
* Preparar dashboard en Power BI.

## Resultado esperado

```text
Visibilidad clara del estado de las excepciones DLP y sus principales riesgos.
```

---

# Fase 8 · Integración operativa

## Objetivo

Conectar el agente con procesos reales de operación, seguimiento y respuesta.

## Mejoras clave

* Crear tickets para excepciones críticas.
* Notificar por Teams o correo.
* Integrar con procesos SOC/GRC.
* Añadir aprobación humana antes de acciones sensibles.
* Registrar evidencias de cierre.
* Integrar con SIEM o herramientas de ticketing.

## Resultado esperado

```text
Agente integrado en el flujo operativo de seguridad y cumplimiento.
```

---

# Fase 9 · Arquitectura multiagente

## Objetivo

Escalar el diseño separando responsabilidades.

## Posible arquitectura

```text
Governance Orchestrator
├── DLP Exception Review Agent
├── DLP Alert Analytics Agent
└── Automation & Reporting Agent
```

## Mejoras clave

* Separar análisis de excepciones.
* Separar análisis de alertas.
* Añadir agente orquestador.
* Añadir agente de reporting.
* Reutilizar componentes para otros casos de gobierno del dato.

## Resultado esperado

```text
Arquitectura modular preparada para más fuentes, más controles y más procesos.
```

---

# Priorización recomendada

| Prioridad | Mejora                                      |
| --------- | ------------------------------------------- |
| Alta      | Actualizar campos del Excel desde el agente |
| Alta      | Validar la correlación de alertas           |
| Alta      | Automatizar recordatorios de caducidad      |
| Alta      | Mejorar scoring de riesgo                   |
| Media     | Añadir formularios de renovación            |
| Media     | Migrar a Dataverse                          |
| Media     | Añadir reporting ejecutivo                  |
| Media     | Conectar con Purview                        |
| Baja      | Integración SIEM/ticketing                  |
| Baja      | Arquitectura multiagente                    |

---

# Principios de evolución

* Mantener revisión humana para decisiones sensibles.
* Automatizar primero cálculos y notificaciones, no remediaciones.
* Priorizar calidad de datos antes que complejidad.
* Mantener trazabilidad de cálculos y decisiones.
* Validar la lógica antes de integrarla con fuentes reales.
* Escalar a Dataverse o Purview cuando el MVP esté estable.
