# Movilidad Post-Cáncer — web

Repositorio de la **web del profesional encargado de cada paciente**. Desde aquí el profesional asigna ejercicios y consulta un dashboard por paciente con sesiones, mediciones y evolución. La [app APK](https://github.com/Luchosqi/movilidad-post-cancer-APK) es para el paciente: muestra los ejercicios asignados y usa la cámara del teléfono para detectar los movimientos durante su ejecución.

## Estado

Planificación inicial. Todavía no se eligió un framework, no hay API desplegada ni se almacenan datos de pacientes. El primer objetivo es simular una [asignación de ejercicio](fixtures/exercise-assignment.example.json) y mostrar el historial de un paciente de prueba a partir de [sesiones sintéticas](fixtures/assessment-session.example.json). Después se conectará el flujo completo con APK.

## Acuerdos de equipo

- [Plan de trabajo compartido](docs/plan-de-trabajo.md): etapas y forma de trabajar.
- [Reparto del Avance 2](docs/avance-2-reparto.md): entregables del 19 de octubre, responsables y fechas internas propuestas.
- [Contrato de integración propuesto](docs/contrato-integracion.md): estructura de las sesiones y reglas de compatibilidad.
- [Propuesta de solución](docs/propuesta-de-solucion.pdf): objetivos y contexto del proyecto.

## Alcance inicial de web

1. Vista del profesional con sus pacientes y un dashboard individual para cada uno.
2. Asignación de ejercicios al paciente y consulta del estado de esas asignaciones.
3. Historial y comparación legible de sesiones, mediciones y evolución de un mismo ejercicio.
4. API y persistencia para entregar asignaciones a APK y recibir las sesiones medidas con la cámara del teléfono, tras acordar stack, acceso y privacidad.
5. Señales visibles de calidad de medición; no inferir diagnósticos ni umbrales clínicos sin validación.

## Forma de contribuir

Crear un issue con el resultado esperado y criterios de aceptación, trabajar en una rama por cambio y pedir revisión a otro integrante antes de integrar. Los cambios al formato de sesión se discuten primero en `docs/contrato-integracion.md` y se coordinan con APK. No subir credenciales, datos reales ni videos de pacientes. Seguir el [flujo GitFlow y las convenciones de commits](CONTRIBUTING.md).

## Estructura actual

- `docs/contrato-integracion.md`: propuesta de intercambio entre ambos repositorios.
- `fixtures/exercise-assignment.example.json`: ejemplo sintético de ejercicio asignado por el profesional.
- `fixtures/assessment-session.example.json`: ejemplo sintético de una sesión realizada por el paciente.

La estructura de código y los comandos de desarrollo se agregarán cuando el equipo elija el stack web.
