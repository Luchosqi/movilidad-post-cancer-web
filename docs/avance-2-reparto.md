# Entrega de especificación y prototipado final: reparto de tareas

**Actualización:** 13 de octubre de 2026. **Fuente del hito:** `Planificación.xlsx` y pauta «Act Especificación y Prototipado Final de Proyecto - ICC710». La entrega próxima es el **19 de octubre**. Las fechas de la tabla son hitos internos propuestos y deben confirmarse con el equipo.

## Estado de la evidencia

La entrevista que el equipo había previsto para el 16 de octubre con Francisco Escobar **no se realizará**. No hay acta de una entrevista anterior entre los documentos entregados. El [documento de entrega](Entrega_Especificacion_y_Prototipado_Final_Movilidad_Post_Cancer.docx) incluye una **simulación explícita** de preguntas y respuestas hipotéticas para revisar decisiones de diseño; no la atribuye a Francisco ni la usa como validación empírica o clínica. El primer ejercicio y sus indicadores siguen pendientes de revisión por un profesional de salud.

## Material integrado

- [Documento Word de entrega](Entrega_Especificacion_y_Prototipado_Final_Movilidad_Post_Cancer.docx): 18 requerimientos funcionales, 10 no funcionales, vínculo con el problema social, matriz de trazabilidad, criterios de aceptación y límites de evidencia.
- [Prototipo navegable de web profesional](https://www.figma.com/proto/oOeWnAmFDW6oCgf7jPyKGG/ContextoSocial-2026-2?node-id=15-2&starting-point-node-id=15%3A2&scaling=scale-down).
- [Prototipo navegable de app del paciente](https://www.figma.com/proto/oOeWnAmFDW6oCgf7jPyKGG/ContextoSocial-2026-2?node-id=16-2&starting-point-node-id=16%3A2&scaling=scale-down).
- [Archivo editable de Figma](https://www.figma.com/design/oOeWnAmFDW6oCgf7jPyKGG/ContextoSocial-2026-2?node-id=0-1): web arriba y móvil abajo, en una sola página.

La revisión del 13 de octubre encontró **32 pantallas de prototipo alcanzables desde dos puntos de inicio, 77 conexiones visibles y ningún destino roto o pantalla aislada**. Se incorporaron estados de autorización, desactivación, compatibilidad de sesiones, cámara, pausa, interrupción y envío rechazado. La paleta final usa blanco, celeste y turquesa pastel. Esta revisión comprueba navegabilidad visual; no verifica una API, medición real por cámara ni controles de seguridad implementados.

## Reparto hasta el 19 de octubre

| Fecha interna propuesta | Responsable | Trabajo y evidencia de cierre |
| --- | --- | --- |
| **14 oct** | Emilia coordina; Luis revisa APK; Cristian revisa web | Revisar el Word contra la pauta, confirmar que cada requisito crítico se relacione con el problema social y corregir términos ambiguos. Registrar decisiones en el documento compartido. |
| **15 oct** | Luis: móvil; Cristian: web; Emilia: lenguaje y accesibilidad | Recorrer ambos enlaces de principio a fin con datos sintéticos. Revisar legibilidad, mensajes, calidad de captura, estados alternativos y correspondencia con la matriz de requisitos. Anotar cualquier corrección y su responsable. |
| **16 oct** | Emilia | Dejar constancia de que la entrevista fue cancelada. Mantener la simulación rotulada como hipótesis; no inventar actas, citas ni confirmaciones. Coordinar una revisión clínica futura del ejercicio y sus métricas. |
| **17 oct** | Luis y Cristian | Revisar el [contrato de integración](contrato-integracion.md): asignación autorizada, identificadores, versión del protocolo, calidad de sesión, reintento y rechazo. Probar con los ejemplos sintéticos; la API sigue pendiente de implementación. |
| **18 oct** | Emilia, con todo el equipo | Subir a la herramienta del curso el Word y los dos enlaces de prototipo. Preparar un recorrido breve que conecte problema, requisitos, flujos, supuestos y límites. Ensayar la presentación. |
| **19 oct** | Todo el equipo | Entregar la versión revisada según la pauta y conservar los enlaces a la misma revisión. |

## Repositorios y forma de trabajo

- **APK:** Luis desarrolla el flujo del paciente, guía de ejercicios, captura por cámara, mediciones y estados de calidad. El [repositorio APK](https://github.com/Luchosqi/movilidad-post-cancer-APK) contiene su alcance y el enlace móvil.
- **Web:** Cristian desarrolla el flujo del profesional, asignaciones, dashboard por paciente, historial y comparación; web alojará la API y persistencia compartidas cuando el equipo elija el stack.
- **Coordinación:** Emilia consolida especificación, evidencia, revisión de lenguaje y entrega. Las decisiones que afecten a ambos productos se reflejan en el contrato compartido.

El equipo trabaja con **GitFlow**, ramas por tarea y **commits atómicos con Conventional Commits**. `main` conserva entregas estables y `develop` integra cambios del próximo avance. Antes de integrar, otro integrante revisa el cambio; no se exige PR. No subir datos reales de pacientes, credenciales ni videos.

## Pendientes explícitos

1. Confirmar hora y medio de entrega en la herramienta del curso.
2. Acordar cuándo y con quién se hará la revisión clínica futura del ejercicio candidato, instrucciones, señales de detención e interpretación de indicadores.
3. Implementar y probar autenticación, autorización, API, persistencia y medición por cámara; Figma representa estos comportamientos solo visualmente.
4. Revisar el [cronograma posterior](plan-de-trabajo.md), incluido el Avance 3 del 30 de noviembre.
