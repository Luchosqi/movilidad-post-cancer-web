# Avance 2: reparto de tareas

**Estado:** propuesta para que Emilia, Luis y Cristian la ajusten en reunión. **Fuente:** `Planificación.xlsx`, hoja `Planificación`, sesiones 16, 18, 19 y 31. **Fecha de referencia:** 6 de octubre de 2026. **Entrevista informada por el equipo:** viernes 16 de octubre con Francisco Escobar, docente stakeholder; hora por definir. Esta entrevista no sustituye una validación clínica.

## Fechas del ramo

| Fecha | Sesión | Qué indica el cronograma | Implicancia para el equipo |
| --- | ---: | --- | --- |
| 9 oct | 16 | Comunicación con el usuario: entrevistas y levantamiento de requerimientos. | Tener preparada la guía de entrevista y confirmar a quién entrevistar. |
| 12 oct | 17 | Suspensión de actividades lectivas. | No contar con una clase para recibir retroalimentación. |
| 16 oct | 18 | Evaluación teórica 2. | También está prevista la entrevista con Francisco Escobar. Confirmar que los horarios no coincidan y registrar hallazgos ese día. |
| **19 oct** | **19** | **Avance 2: propuesta final + requerimientos + Figma.** | **Entrega próxima del proyecto.** |
| **30 nov** | **31** | **Avance 3: prototipo final + documentación.** | Hito de implementación posterior al Avance 2. |

Las fechas proceden de las celdas `D21`, `D22`, `D23`, `D24` y `D36` del cronograma. El documento no especifica hora de entrega ni pauta de evaluación detallada; deben confirmarse con el docente.

## Qué debe existir para el 19 de octubre

1. **Propuesta final:** problema, usuarios, objetivo, alcance del prototipo, flujo APK ↔ web, límites de la herramienta y cambios motivados por entrevistas o revisión de la contraparte.
2. **Requerimientos trazables:** fuente de cada necesidad, lista priorizada de requerimientos funcionales y no funcionales, criterios de aceptación y preguntas aún abiertas. Señalar qué afirmaciones están validadas y cuáles son hipótesis.
3. **Figma:** pantallas enlazadas para el recorrido del paciente (inicio, guía, medición, resultado) y del profesional (historial y comparación). Anotar qué requerimiento cubre cada flujo; un prototipo visual no implica funcionalidad implementada.
4. **Presentación:** recorrido breve que conecte problema → evidencia → solución → requerimientos → prototipo → plan hasta el 30 de noviembre. Revisar que las tres piezas cuenten la misma versión del proyecto.

## Dueños propuestos y entregas

| Trabajo | Responsable principal | Apoyo/revisión | Entrega verificable | Fecha interna propuesta |
| --- | --- | --- | --- | --- |
| [Contacto con contraparte, guía de entrevista y registro de respuestas](https://github.com/Luchosqi/movilidad-post-cancer-web/issues/2) | Emilia | Luis y Cristian revisan preguntas técnicas | Guía, notas fechadas y lista de hallazgos de Francisco Escobar. Separar sus aportes de la validación clínica pendiente. | Guía 8 oct; entrevista 16 oct; síntesis 17 oct. |
| [Protocolo del primer ejercicio y necesidades de la app paciente](https://github.com/Luchosqi/movilidad-post-cancer-APK/issues/2) | Luis | Emilia revisa lenguaje y recoge preguntas para validación clínica posterior; Cristian revisa datos | Ejercicio candidato, pasos, indicadores a explorar, condiciones de calidad y requisitos APK con criterios de aceptación. Todo queda sujeto a revisión clínica. | Borrador 11 oct; revisión 14 oct; ajuste tras entrevista 17 oct. |
| [Flujo profesional, datos y necesidades de web](https://github.com/Luchosqi/movilidad-post-cancer-web/issues/3) | Cristian | Emilia recoge comentarios de Francisco; Luis revisa el intercambio | Casos de uso del profesional, requisitos de historial/comparación, campos mínimos y riesgos de acceso/privacidad. | Borrador 11 oct; revisión 14 oct; ajuste tras entrevista 17 oct. |
| [Síntesis de requerimientos y propuesta final](https://github.com/Luchosqi/movilidad-post-cancer-web/issues/2) | Emilia | Luis y Cristian aportan y revisan su sección | Documento único con prioridades, fuentes, decisiones y preguntas pendientes; versión final de la propuesta. | Borrador 14 oct; cierre tras entrevista 18 oct. |
| [Prototipo Figma de APK](https://github.com/Luchosqi/movilidad-post-cancer-APK/issues/2) | Luis | Emilia revisa comprensibilidad; Cristian revisa continuidad de datos | Flujo navegable del paciente con estados de error/calidad y anotaciones de requerimientos. | Borrador 15 oct; ajuste 17 oct. |
| [Prototipo Figma de web](https://github.com/Luchosqi/movilidad-post-cancer-web/issues/3) | Cristian | Emilia revisa lectura para profesionales; Luis revisa métricas | Flujo navegable de historial y comparación, con calidad de medición visible. | Borrador 15 oct; ajuste 17 oct. |
| [Integración de Figma, presentación y ensayo](https://github.com/Luchosqi/movilidad-post-cancer-web/issues/4) | Emilia coordina | Luis y Cristian presentan y corrigen sus partes | Un único enlace de Figma, presentación y ensayo cronometrado; verificación contra el texto exacto del Avance 2. | Integración inicial 15 oct; versión final y ensayo 18 oct. |

Las fechas internas son objetivos sugeridos para dejar margen de revisión antes del 19 de octubre. La entrevista con Francisco Escobar está prevista para el 16 de octubre: hasta registrar y sintetizar sus respuestas, los requerimientos y prototipos son borradores basados en hipótesis. Sus comentarios orientarán el proyecto, pero el protocolo y las métricas seguirán pendientes de revisión por profesionales de salud. Si se reprograma, registrar la limitación y distinguir lo inferido de lo confirmado.

## Reparto por repositorio

- **APK:** Luis abre tareas para protocolo, requisitos de captura/medición y flujo Figma del paciente. No necesita cerrar un modelo de pose antes del Avance 2; sí justificar viabilidad y riesgos.
- **web:** Cristian abre tareas para requerimientos del profesional, datos, flujo Figma y revisión del [contrato de integración](contrato-integracion.md).
- **Coordinación compartida:** Emilia mantiene la propuesta final, el registro de entrevistas y la presentación en `web/docs` para que todos trabajen sobre una versión. Los PR de cambios de alcance o contrato se revisan entre repositorios.

## Preguntas para cerrar en la próxima reunión

- ¿A qué hora será la entrevista con Francisco Escobar y con qué consentimiento se registrarán notas? ¿Coincide con la evaluación teórica?
- ¿Qué ejercicio se tomará como primer caso y qué medición podría ser útil? ¿Quién coordinará la revisión posterior con un profesional de salud?
- ¿Qué pide exactamente la pauta del Avance 2 sobre cantidad de requerimientos, formato de Figma y duración de presentación?
- ¿Quién creará el archivo Figma y compartirá acceso de edición al equipo? ¿Dónde se guardará el enlace?
- ¿Qué horarios reales tiene cada integrante entre el 9 y el 19 de octubre, considerando la evaluación teórica del 16?
