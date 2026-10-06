# Movilidad Post-Cáncer — web

Repositorio de la interfaz para profesionales y del futuro servicio de sesiones del proyecto **Movilidad Post-Cáncer**. La propuesta del curso plantea una app para el paciente, una herramienta clínica y un panel de seguimiento. Este repositorio agrupa las dos vistas profesionales; [APK](https://github.com/Luchosqi/movilidad-post-cancer-APK) se encarga de la captura y medición en Android.

## Estado

Planificación inicial. Todavía no se eligió un framework, no hay API desplegada ni se almacenan datos de pacientes. El primer objetivo es mostrar el historial de una persona de prueba a partir de [datos sintéticos](fixtures/assessment-session.example.json) y después conectar un flujo completo con APK.

## Acuerdos de equipo

- [Plan de trabajo compartido](docs/plan-de-trabajo.md): etapas, responsabilidades, forma de trabajar y decisiones para la primera reunión.
- [Contrato de integración propuesto](docs/contrato-integracion.md): estructura de las sesiones y reglas de compatibilidad.
- [Propuesta de solución](docs/propuesta-de-solucion.pdf): objetivos y contexto del proyecto.

## Alcance inicial de web

1. Vista de un profesional con identificador de prueba e historial de sesiones.
2. Comparación legible de mediciones del mismo ejercicio y lado en distintos momentos.
3. API y persistencia para recibir las sesiones de APK, tras acordar stack, acceso y privacidad.
4. Señales visibles de calidad de medición; no inferir diagnósticos ni umbrales clínicos sin validación.

## Forma de contribuir

Crear un issue con el resultado esperado y criterios de aceptación, trabajar en una rama por cambio y abrir un PR para revisión por otro integrante. Los cambios al formato de sesión se discuten primero en `docs/contrato-integracion.md` y se coordinan con APK. No subir credenciales, datos reales ni videos de pacientes.

## Estructura actual

- `docs/contrato-integracion.md`: propuesta de intercambio entre ambos repositorios.
- `fixtures/assessment-session.example.json`: ejemplo sintético para desarrollar y probar la vista.

La estructura de código y los comandos de desarrollo se agregarán cuando el equipo elija el stack web.
