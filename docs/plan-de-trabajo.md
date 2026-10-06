# Plan de trabajo compartido

**Estado:** propuesta para discutir con el equipo. **Fuente:** [Propuesta de solución](propuesta-de-solucion.pdf) y [README inicial de APK](https://github.com/Luchosqi/movilidad-post-cancer-APK/blob/main/README.md). **Actualizado:** 2026-10-06. Para el próximo hito del ramo, ver el [reparto del Avance 2](avance-2-reparto.md).

## Resultado que buscamos

Un prototipo de apoyo a la evaluación de movilidad, no un diagnóstico: una persona realiza un ejercicio guiado, la app registra mediciones de una sesión y un profesional autorizado puede revisar la evolución. Los ejercicios, la interpretación de los indicadores y la forma de validarlos requieren acuerdo con profesionales de salud antes de usarse con pacientes.

### Corte mínimo para demostrar integración

1. Un ejercicio elegido y revisado con la contraparte, con instrucciones y criterios para iniciar/detener la prueba.
2. Una sesión capturada en Android con un indicador definido y una señal de calidad de la medición.
3. Envío de la sesión mediante el [contrato de integración](https://github.com/Luchosqi/movilidad-post-cancer-web/blob/main/docs/contrato-integracion.md).
4. Una vista web que muestre el historial y compare al menos dos sesiones del mismo identificador de prueba.
5. Demostración con datos sintéticos. Cualquier prueba con personas o datos reales queda sujeta a la revisión de la contraparte y a un acuerdo de privacidad.

## Responsabilidades de los repositorios

| Repositorio | Es responsable de | Fuera de su responsabilidad principal |
| --- | --- | --- |
| [APK](https://github.com/Luchosqi/movilidad-post-cancer-APK) | Experiencia del paciente en Flutter/Android, guía del ejercicio, captura de cámara y estimación de pose, cálculo local de métricas, revisión de calidad y envío de sesiones. | Gestión de pacientes, panel clínico y almacenamiento central. |
| [web](https://github.com/Luchosqi/movilidad-post-cancer-web) | Interfaz para profesionales, historial y gráficos de seguimiento; servicio/API y persistencia compartida cuando se acuerde el stack. Mantiene el contrato de integración. | Captura de cámara y cálculo de pose en Android. |

La prueba de concepto con webcam/computador descrita en la propuesta se hace primero en APK para que el algoritmo y sus pruebas permanezcan junto al futuro cliente Android. Si esa opción resulta inviable, el equipo documentará el cambio antes de mover código entre repositorios.

## Secuencia de trabajo

| Etapa | Entrega verificable | APK | web / coordinación |
| --- | --- | --- | --- |
| 0. Acordar alcance | Ejercicio inicial, indicadores, condiciones de prueba, flujo de usuario y criterios de aceptación aprobados por el equipo y revisados por la contraparte. | Proponer protocolo y comprobar viabilidad de cámara/pose. | Proponer vista del profesional y datos mínimos; Emilia coordina la revisión clínica. |
| 1. Prueba de concepto | Un video o webcam de prueba produce mediciones repetibles sobre material de prueba no clínico; se registran límites y errores. | Implementar y evaluar la captura y el cálculo. | Construir una vista con el ejemplo JSON del contrato, sin depender aún de la app. |
| 2. Integración vertical | Una sesión de prueba sale de Android, llega a la API y aparece en el historial web. | App de un ejercicio y envío con manejo de errores. | API, persistencia y vista de sesiones. |
| 3. Seguimiento y validación | Dos o más sesiones comparables, revisión de calidad, pruebas de uso y devolución de profesionales. | Mejorar guía, accesibilidad y consistencia de medición. | Tendencias, filtros necesarios y control de acceso. Emilia coordina la validación. |

No se agregan más ejercicios ni se fijan umbrales clínicos hasta comprobar la primera integración y revisarlos con la contraparte.

## Reparto inicial para conversar

Se toma la distribución de la propuesta, sin convertirla en asignación permanente:

- **Emilia Toro:** coordinación de iteración 1, entrevistas, contacto con contraparte y validación clínica. Recoge las decisiones pendientes y los criterios de aceptación.
- **Luis Jaramillo:** protocolo del ejercicio, indicadores y prueba de concepto de pose en APK. Coordina con web el significado y formato de cada métrica.
- **Cristian Sandoval:** registro, visualización e historial en web. Propone persistencia y API junto con Luis.
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
- ¿Quién usa cada pantalla: paciente, kinesiólogo u otro profesional? ¿Qué necesita ver para comparar sesiones?
- ¿La primera integración requiere cuentas reales o basta con identificadores de prueba? Definir autorización, consentimiento, retención y eliminación antes de datos reales.
- ¿Qué stack y alojamiento usará web para API y base de datos? Elegirlo tras probar el flujo mínimo y las habilidades del equipo.
- ¿Qué fechas, entregables y criterios exige el curso para cada iteración? Tras confirmarlos, convertir las etapas anteriores en hitos e issues con responsables.
