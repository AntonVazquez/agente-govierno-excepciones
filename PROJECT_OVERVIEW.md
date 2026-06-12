# 📘 Project Overview

## 🧩 Descripción

**DLP Exception Governance Agent** es un agente de **Microsoft Copilot Studio** diseñado para apoyar la revisión de excepciones DLP.

El agente combina dos perspectivas:

```text
Inventario de excepciones DLP
+
Actividad real de alertas DLP
```

Con esta información, ayuda a los equipos de seguridad, protección del dato y gobierno a decidir qué excepciones deben revisarse, renovarse, retirarse o escalarse.

---

## ❗ Problema que resuelve

Las excepciones DLP suelen aprobarse para cubrir necesidades concretas de negocio.
El problema aparece cuando esas excepciones no se revisan de forma periódica.

| Riesgo                | Ejemplo                                                  |
| --------------------- | -------------------------------------------------------- |
| Excepciones sin uso   | Una excepción sigue activa aunque ya no genera actividad |
| Excepciones caducadas | Una excepción vencida sigue teniendo alertas asociadas   |
| Falta de evidencia    | No está claro si debe renovarse o retirarse              |
| Revisión manual lenta | El análisis depende de revisar Excel y exports separados |
| Priorización limitada | No siempre se sabe qué revisar primero                   |

---

## 🎯 Objetivo del MVP

El MVP demuestra que un agente puede:

1. Leer un inventario de excepciones DLP.
2. Leer un export de alertas DLP.
3. Correlacionar ambos datasets.
4. Calcular alertas relacionadas en los últimos 30 días.
5. Priorizar excepciones que requieren revisión.
6. Proponer acciones recomendadas.

---

## 🏗️ Diseño del MVP

Para mantener la solución simple y demostrable, el MVP utiliza:

| Decisión                            | Motivo                                |
| ----------------------------------- | ------------------------------------- |
| Un único agente de Copilot Studio   | Menor complejidad para demo           |
| Dos ficheros Excel                  | Fácil de entender y modificar         |
| Excepciones solo a usuarios         | Correlación más clara                 |
| Correlación por usuario y directiva | Lógica simple y explicable            |
| Ventana de 30 días                  | Actividad reciente y fácil de validar |

---

## 👥 Usuarios objetivo

El agente está pensado para:

* Equipos de seguridad.
* Administradores DLP.
* Equipos de protección del dato.
* Equipos GRC.
* SOC o analistas de seguridad.
* Responsables de cumplimiento.

---

## 💡 Valor del proyecto

El valor principal no está en consultar un Excel, sino en cruzar el estado de las excepciones con actividad DLP reciente.

Esto permite responder preguntas como:

| Pregunta                                              | Resultado esperado                  |
| ----------------------------------------------------- | ----------------------------------- |
| ¿Qué excepciones siguen generando alertas?            | Identificar actividad real          |
| ¿Qué excepciones activas no tienen uso reciente?      | Valorar retirada                    |
| ¿Qué excepciones caducadas siguen teniendo actividad? | Escalar revisión                    |
| ¿Qué casos deberían revisarse primero?                | Priorizar esfuerzo                  |
| ¿Qué acción debería tomar el equipo?                  | Renovar, revisar, retirar o escalar |

---

## 🔄 Flujo funcional del MVP

```text
1. Leer excepciones DLP
        ↓
2. Leer export de alertas DLP
        ↓
3. Correlacionar por usuario y directiva
        ↓
4. Calcular Alertas30Dias
        ↓
5. Evaluar estado y riesgo
        ↓
6. Recomendar acción
```

---

## 🚀 Evolución futura

El MVP puede evolucionar incorporando:

| Mejora futura                          | Valor                            |
| -------------------------------------- | -------------------------------- |
| Conexión directa con Microsoft Purview | Menos carga manual               |
| Power Automate                         | Notificaciones y actualizaciones |
| Microsoft Forms                        | Renovación de excepciones        |
| Dataverse                              | Modelo de datos más robusto      |
| Teams                                  | Comunicación con responsables    |
| Dashboards                             | Seguimiento ejecutivo            |
| Arquitectura multiagente               | Separación por dominios          |
| Integración con ticketing/SIEM         | Operación más completa           |

---

## 📌 Resumen

Este proyecto demuestra cómo **Copilot Studio** puede apoyar un proceso real de gobierno de seguridad: la revisión de excepciones DLP.

El MVP mantiene un diseño simple:

```text
Excepciones
+
Alertas
+
Correlación
+
Priorización
+
Recomendación
```

La solución está pensada para ser fácil de demostrar en un hackathon y suficientemente clara para evolucionar después.
