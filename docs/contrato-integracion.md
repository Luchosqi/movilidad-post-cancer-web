# Contrato de integración APK ↔ web

**Estado:** propuesta v0.1 para revisión del equipo, 2026-10-06. **Responsable de edición:** web; cualquier cambio que afecte a APK se acuerda en un issue y se revisa por ambos lados antes de integrar.

## Flujo previsto

El profesional encargado asigna ejercicios a cada paciente en web y consulta su dashboard individual. APK muestra al paciente sus ejercicios asignados; al realizarlos, la cámara del teléfono detecta movimientos y la app calcula una sesión con indicadores y calidad. La sesión vuelve a web para el seguimiento del profesional. La prueba de integración usa exclusivamente datos sintéticos.

```
Profesional → web (asignación) → API → APK del paciente (cámara y movimientos)
Profesional ← web (dashboard por paciente) ← API ← APK (sesión medida)
```

La API, autenticación, base de datos, catálogo de instrucciones y hospedaje aún no están elegidos. Este documento fija primero el significado de los datos para poder avanzar en ambos repositorios. No implica que exista ya un servicio operativo.

## Mensaje `exercise-assignment` v0.1

[Ejemplo sintético](../fixtures/exercise-assignment.example.json). Representa un ejercicio que el profesional asigna desde web a un paciente. APK consultará las asignaciones del paciente autorizado y mostrará las instrucciones correspondientes a `exercise_id` y `protocol_version`. La dosificación, instrucciones y reglas clínicas del ejercicio quedan pendientes de revisión por profesionales de salud.

| Campo | Tipo y significado |
| --- | --- |
| `schema_version` | Cadena fija `0.1`. |
| `assignment_id` | UUID de la asignación, generado por web. |
| `patient_id` | Identificador seudónimo del paciente destinatario. |
| `professional_id` | Identificador seudónimo del profesional que asigna. |
| `exercise_id` | Código del ejercicio del catálogo acordado por el equipo. |
| `protocol_version` | Versión de las instrucciones y forma de medir ese ejercicio. |
| `side` | `left`, `right`, `bilateral` o `none`, según el ejercicio. |
| `assigned_at` | Fecha y hora ISO 8601 en UTC. |

## Mensaje `assessment-session` v0.1

[Ejemplo completo](../fixtures/assessment-session.example.json). Una sesión registra la ejecución medida de un ejercicio y un lado; las comparaciones solo tienen sentido entre sesiones con el mismo ejercicio, lado, métrica, unidad y versión de protocolo.

| Campo | Tipo y significado |
| --- | --- |
| `schema_version` | Cadena fija `0.1`. Permite detectar cambios incompatibles. |
| `session_id` | UUID de la sesión, generado por APK. Reenvíos con el mismo ID no deben crear duplicados. |
| `assignment_id` | UUID de la asignación que originó la sesión. Opcional en la prueba de concepto; obligatorio para sesiones de ejercicios asignados. |
| `patient_id` | Identificador seudónimo de prueba. La relación con una persona real queda fuera del mensaje y exige diseño de privacidad. |
| `exercise_id` | Código estable del ejercicio, acordado con la contraparte. El ejemplo usa un código ficticio. |
| `protocol_version` | Versión de instrucciones y método; se guarda para comparar mediciones compatibles. |
| `side` | `left`, `right`, `bilateral` o `none`, según el ejercicio. |
| `recorded_at` | Fecha y hora ISO 8601 en UTC. |
| `metrics` | Lista de `{name, value, unit}`. Los nombres, unidades y cálculo deben definirse por ejercicio; no hay umbrales diagnósticos en este contrato. |
| `quality` | `usable`, `review` o `invalid`, más códigos de causa opcionales. La web muestra este estado y excluye `invalid` de comparaciones automáticas. |
| `measurement_version` | Identifica la versión del algoritmo/modelo que produjo las métricas. |

Los mensajes no incluyen nombre, RUT, correo, diagnóstico, imagen ni video. Los valores de los ejemplos son inventados; no representan resultados clínicos ni rangos normales.

## Reglas de integración a confirmar

- **Idempotencia:** `assignment_id` identifica la asignación y `session_id` identifica el envío de la sesión; los reintentos no deben crear duplicados.
- **Relación:** web solo entrega a APK las asignaciones del paciente autorizado. Cada sesión de un ejercicio asignado debe conservar su `assignment_id` para aparecer en el dashboard de ese paciente.
- **Validación:** web rechaza versiones desconocidas, campos obligatorios ausentes, valores no numéricos, unidades no acordadas y timestamps inválidos. El error debe indicar qué corregir sin exponer datos sensibles.
- **Compatibilidad:** añadir campos opcionales puede conservar la versión; cambiar significado, unidad o nombre de una métrica requiere nueva versión y coordinación entre repositorios.
- **Calidad:** APK calcula el estado de calidad según criterios aún por definir; web lo conserva y lo presenta sin reinterpretarlo.
- **Comparación:** web agrupa por paciente de prueba, `exercise_id`, `side`, nombre/unidad de métrica y `protocol_version`. No calcula conclusiones clínicas.
- **Seguridad:** antes de datos reales, definir autenticación de paciente y profesional, qué profesional está a cargo de cada paciente, autorización por paciente, cifrado en tránsito, retención, eliminación y consentimiento con la contraparte.

## Siguiente acuerdo técnico

En la primera reunión de integración, Luis y Cristian deben cerrar el ejercicio inicial, cómo llega una asignación a APK, nombres y unidades de las métricas, criterios de calidad y respuesta de la API. Luego crear issues enlazados para la asignación y el retorno de sesiones. La implementación y las pruebas deben usar los ejemplos sintéticos de este repositorio.
