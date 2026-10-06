# Contrato de integración APK ↔ web

**Estado:** propuesta v0.1 para revisión del equipo, 2026-10-06. **Responsable de edición:** web; cualquier cambio que afecte a APK se acuerda en un issue y se revisa por ambos lados antes de integrar.

## Flujo previsto

APK guía el ejercicio y calcula una sesión con indicadores y calidad. Web recibe la sesión, la conserva según las reglas de acceso y retención que acuerde el equipo, y muestra el historial a un profesional autorizado. La prueba de integración usa exclusivamente datos sintéticos.

```
APK (captura y medición) → API de web (validación y almacenamiento) → panel profesional (historial)
```

La API, autenticación, base de datos y hospedaje aún no están elegidos. Este documento fija primero el significado de los datos para poder avanzar en ambos repositorios. No implica que exista ya un servicio operativo.

## Mensaje `assessment-session` v0.1

[Ejemplo completo](../fixtures/assessment-session.example.json). Una sesión registra una evaluación de un ejercicio y un lado; las comparaciones solo tienen sentido entre sesiones con el mismo ejercicio, lado, métrica, unidad y versión de protocolo.

| Campo | Tipo y significado |
| --- | --- |
| `schema_version` | Cadena fija `0.1`. Permite detectar cambios incompatibles. |
| `session_id` | UUID de la sesión, generado por APK. Reenvíos con el mismo ID no deben crear duplicados. |
| `patient_id` | Identificador seudónimo de prueba. La relación con una persona real queda fuera del mensaje y exige diseño de privacidad. |
| `exercise_id` | Código estable del ejercicio, acordado con la contraparte. El ejemplo usa un código ficticio. |
| `protocol_version` | Versión de instrucciones y método; se guarda para comparar mediciones compatibles. |
| `side` | `left`, `right`, `bilateral` o `none`, según el ejercicio. |
| `recorded_at` | Fecha y hora ISO 8601 en UTC. |
| `metrics` | Lista de `{name, value, unit}`. Los nombres, unidades y cálculo deben definirse por ejercicio; no hay umbrales diagnósticos en este contrato. |
| `quality` | `usable`, `review` o `invalid`, más códigos de causa opcionales. La web muestra este estado y excluye `invalid` de comparaciones automáticas. |
| `measurement_version` | Identifica la versión del algoritmo/modelo que produjo las métricas. |

El mensaje no incluye nombre, RUT, correo, diagnóstico, imagen ni video. Los valores del archivo de ejemplo son inventados; no representan resultados clínicos ni rangos normales.

## Reglas de integración a confirmar

- **Idempotencia:** `session_id` identifica un envío; APK puede reintentar sin duplicar la sesión.
- **Validación:** web rechaza versiones desconocidas, campos obligatorios ausentes, valores no numéricos, unidades no acordadas y timestamps inválidos. El error debe indicar qué corregir sin exponer datos sensibles.
- **Compatibilidad:** añadir campos opcionales puede conservar la versión; cambiar significado, unidad o nombre de una métrica requiere nueva versión y coordinación entre repositorios.
- **Calidad:** APK calcula el estado de calidad según criterios aún por definir; web lo conserva y lo presenta sin reinterpretarlo.
- **Comparación:** web agrupa por paciente de prueba, `exercise_id`, `side`, nombre/unidad de métrica y `protocol_version`. No calcula conclusiones clínicas.
- **Seguridad:** antes de datos reales, definir autenticación de paciente y profesional, autorización por paciente, cifrado en tránsito, retención, eliminación y consentimiento con la contraparte.

## Siguiente acuerdo técnico

En la primera reunión de integración, Luis y Cristian deben cerrar el ejercicio inicial, nombres y unidades de las métricas, criterios de calidad y respuesta de la API. Luego crear un issue en web para el endpoint y otro en APK para el envío, enlazados entre sí. La implementación y pruebas deben utilizar el mismo ejemplo de este repositorio.
