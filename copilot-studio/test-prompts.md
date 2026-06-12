# Prompts de prueba

## 1. Revisar excepciones activas

```text
Muéstrame las excepciones activas y resume su estado.
```

Validar que:

* Lista solo excepciones activas.
* Incluye solicitante, directiva, fecha de caducidad y estado.
* No calcula riesgo si la excepción no está lista.

---

## 2. Calcular alertas recientes

```text
Calcula las alertas de los últimos 30 días para cada excepción usando el export de alertas DLP.
```

Validar que:

* Cruza `Solicitante` con `Usuario`.
* Cruza `DirectivaDLP` con `Directiva`.
* Cuenta solo alertas de los últimos 30 días.
* Genera el valor de `Alertas30Dias`.

---

## 3. Actualizar inventario

```text
Completa la columna Alertas30Dias y FechaUltimaActividad en el Excel de excepciones.
```

Validar que:

* Usa el export de alertas como fuente.
* Actualiza solo los campos solicitados si existe acción disponible.
* Si no puede actualizar, devuelve una tabla con los valores calculados.

---

## 4. Detectar excepciones sin uso

```text
¿Qué excepciones activas no tienen actividad en los últimos 30 días?
```

Validar que:

* Detecta excepciones activas con `Alertas30Dias = 0`.
* Recomienda `Retirar` o `Revisar`.
* No incluye excepciones pendientes o rechazadas.

---

## 5. Detectar caducadas con actividad

```text
¿Qué excepciones caducadas siguen generando alertas DLP?
```

Validar que:

* Identifica excepciones caducadas.
* Comprueba si tienen alertas recientes relacionadas.
* Recomienda `Escalar`.

---

## 6. Priorizar revisión

```text
Prioriza las excepciones que deberían revisarse primero.
```

Validar que:

* Ordena por riesgo.
* Tiene en cuenta caducidad, volumen de alertas, tipo de dato y canal.
* Explica el motivo de la prioridad.

---

## 7. Recomendar acciones

```text
Recomienda una acción para cada excepción activa.
```

Validar que usa solo estas acciones:

```text
Renovar
Revisar
Retirar
Escalar
Sin acción inmediata
```

---

## 8. Resumen ejecutivo

```text
Genera un resumen ejecutivo del estado de las excepciones DLP.
```

Validar que incluye:

* Excepciones activas.
* Excepciones caducadas.
* Excepciones de mayor riesgo.
* Excepciones sin actividad reciente.
* Próximos pasos recomendados.

---

## 9. Control de preparación

```text
Evalúa el riesgo de todas las excepciones, incluidas las pendientes de aprobación.
```

Validar que:

* No evalúa excepciones pendientes, rechazadas o incompletas.
* Explica qué condición falta para poder evaluarlas.

---

## 10. Precisión de correlación

```text
Para cada excepción, dime qué alertas has contado y por qué.
```

Validar que:

* Explica el cruce por `Solicitante` + `DirectivaDLP`.
* No cuenta alertas de otros usuarios.
* No cuenta alertas de otras directivas.
* No cuenta alertas fuera de los últimos 30 días.
