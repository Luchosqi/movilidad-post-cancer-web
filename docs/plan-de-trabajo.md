# Plan de trabajo compartido

**Estado:** propuesta para discutir con el equipo. **Fuente:** [Propuesta de solución](propuesta-de-solucion.pdf) y [README inicial de APK](https://github.com/Luchosqi/movilidad-post-cancer-APK/blob/main/README.md). **Actualizado:** 2026-10-06. La división entre profesional y paciente incorpora la aclaración posterior del equipo; el PDF conserva la propuesta inicial. Para el próximo hito del ramo, ver el [reparto del Avance 2](avance-2-reparto.md).

## Resultado que buscamos

Un prototipo de apoyo a la movilidad, no un diagnóstico: el profesional encargado asigna un ejercicio desde la web, el paciente lo realiza con guía en la app y la cámara del teléfono detecta sus movimientos. La app registra una sesión y el profesional revisa su evolución en el dashboard individual. Los ejercicios, la interpretación de los indicadores y la forma de validarlos requieren acuerdo con profesionales de salud antes de usarse con pacientes.

### Corte mínimo para demostrar integración

1. Un ejercicio elegido y revisado con la contraparte, con instrucciones y criterios para iniciar/detener la prueba.
2. Una asignación creada por el profesional en web y visible para el paciente en APK.
3. Una sesión capturada con la cámara de Android, con detección de movimientos, un indicador definido y una señal de calidad de la medición.
4. Envío de la sesión vinculada a la asignación mediante el [contrato de integración](https://github.com/Luchosqi/movilidad-post-cancer-web/blob/main/docs/contrato-integracion.md).
5. Un dashboard web por paciente que muestre el historial y compare al menos dos sesiones del mismo identificador de prueba.
6. Demostración con datos sintéticos. Cualquier prueba con personas o datos reales queda sujeta a la revisión de la contraparte y a un acuerdo de privacidad.

## Responsabilidades de los repositorios

| Repositorio | Es responsable de | Fuera de su responsabilidad principal |
| --- | --- | --- |
| [APK](https://github.com/Luchosqi/movilidad-post-cancer-APK) | App del paciente en Flutter/Android: recibe ejercicios asignados por su profesional, guía su ejecución, usa la cámara del teléfono para detectar movimientos, calcula métricas y calidad, y envía las sesiones. | Asignación de ejercicios, gestión de pacientes, dashboard clínico y almacenamiento central. |
| [web](https://github.com/Luchosqi/movilidad-post-cancer-web) | Herramienta del profesional encargado: pacientes a cargo, asignación de ejercicios y dashboard individual con sesiones, mediciones y evolución. Mantiene el contrato y, cuando se acuerde el stack, la API y persistencia compartida. | Captura de cámara y detección de movimientos en el teléfono. |

La prueba de concepto con webcam/computador descrita en la propuesta se hace primero en APK para que el algoritmo y sus pruebas permanezcan junto al futuro cliente Android. Si esa opción resulta inviable, el equipo documentará el cambio antes de mover código entre repositorios.

## Secuencia de trabajo

| Etapa | Entrega verificable | APK | web / coordinación |
| --- | --- | --- | --- |
| 0. Acordar alcance | Ejercicio inicial, asignación, indicadores, condiciones de prueba y criterios de aceptación aprobados por el equipo y revisados por la contraparte. | Proponer protocolo y comprobar viabilidad de cámara/pose. | Proponer flujo de asignación, dashboard por paciente y datos mínimos; Emilia coordina la revisión clínica. |
| 1. Prueba de concepto | Un video o webcam de prueba produce mediciones repetibles sobre material de prueba no clínico; se registran límites y errores. | Implementar y evaluar la captura y detección de movimientos. | Construir asignación y dashboard con ejemplos JSON, sin depender aún de la app. |
| 2. Integración vertical | El profesional asigna un ejercicio, APK lo muestra, el paciente lo realiza y la sesión aparece en su dashboard web. | Cargar la asignación, detectar movimientos con cámara y enviar la sesión con manejo de errores. | API, persistencia, asignación y dashboard por paciente. |
| 3. Seguimiento y validación | Dos o más sesiones comparables, revisión de calidad, pruebas de uso y devolución de profesionales. | Mejorar guía, accesibilidad y consistencia de medición. | Tendencias, filtros necesarios y control de acceso. Emilia coordina la validación. |

No se agregan más ejercicios ni se fijan umbrales clínicos hasta comprobar la primera integración y revisar el protocolo y las métricas con profesionales de salud.

## Reparto inicial para conversar

Se toma la distribución de la propuesta, sin convertirla en asignación permanente:

- **Emilia Toro:** coordinación de iteración 1, entrevistas, contacto con contraparte y validación clínica. Recoge las decisiones pendientes y los criterios de aceptación.
- **Luis Jaramillo:** protocolo del ejercicio, indicadores y prueba de concepto de pose en APK. Coordina con web el significado y formato de cada métrica.
- **Cristian Sandoval:** asignación de ejercicios, registro, visualización y dashboard por paciente en web. Propone persistencia y API junto con Luis.
- **Todo el equipo:** revisión cruzada del contrato, pruebas integradas y decisiones de privacidad.

La rotación de coordinación sigue la descrita en el README de APK: Emilia, Luis y Cristian.

## Cómo trabajamos en dos repositorios

1. Cada tarea tiene un repositorio dueño y un issue allí. Si toca a ambos, se crean dos issues enlazados con un mismo nombre de hito; cada uno indica qué espera del otro.
2. La API y el formato de sesión se acuerdan mediante una tarea y revisión del [contrato de web](https://github.com/Luchosqi/movilidad-post-cancer-web/blob/main/docs/contrato-integracion.md) antes de implementar cambios incompatibles. Web publica un ejemplo JSON; APK lo usa para probar su envío.
3. Cada repositorio sigue [GitFlow y commits atómicos](../CONTRIBUTING.md): `feature/*` sale de `develop`, las entregas pasan por `release/*` hacia `main` y otro integrante revisa antes de integrar. Los PR son opcionales.
4. En cada reunión se revisan bloqueos, contratos pendientes, demostración del incremento y próximo responsable de cada tarea. Se anota la decisión en el issue correspondiente.
5. No se suben datos identificables de pacientes, videos clínicos, credenciales ni bases reales. Las pruebas compartidas usan datos sintéticos y el despliegue requiere definir acceso, retención y consentimiento.

## Primera reunión: decisiones que faltan

- ¿Qué ejercicio y articulación cubrirá el primer corte? ¿Qué profesional validará instrucciones, seguridad y utilidad de la medición?
- ¿Qué indicador exacto se calcula y cuándo una medición se marca como no confiable? No asumir valores normales ni diagnósticos.
- ¿Qué profesional tendrá pacientes a cargo y podrá asignar ejercicios? ¿Qué debe mostrar el dashboard individual para comparar sesiones?
- ¿La primera integración requiere cuentas reales o basta con identificadores de prueba? Definir autorización, consentimiento, retención y eliminación antes de datos reales.
- ¿Qué stack y alojamiento usará web para API y base de datos? Elegirlo tras probar el flujo mínimo y las habilidades del equipo.
- ¿Qué fechas, entregables y criterios exige el curso para cada iteración? Tras confirmarlos, convertir las etapas anteriores en hitos e issues con responsables.
