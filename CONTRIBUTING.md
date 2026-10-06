# Flujo de trabajo del equipo

Este flujo se aplica por igual a `movilidad-post-cancer-APK` y `movilidad-post-cancer-web`. Las tareas y decisiones se registran en el repositorio que es dueño del cambio. El [plan compartido](https://github.com/Luchosqi/movilidad-post-cancer-web/blob/main/docs/plan-de-trabajo.md) define los límites entre ambos.

## GitFlow

- **`main`:** versión estable que se puede mostrar o entregar. Recibe cambios desde `release/*` y `hotfix/*`. Se etiqueta una versión cuando haya una entrega real.
- **`develop`:** integración de trabajo aprobado para el siguiente avance. Es la base de nuevas funcionalidades.
- **`feature/<issue>-<tema>`:** nace de `develop` y vuelve a `develop` cuando la tarea cumple sus criterios de aceptación. Incluye documentación o pruebas necesarias para ese cambio. Ejemplo: `feature/2-protocolo-inicial`.
- **`release/<version>`:** nace de `develop` al preparar una entrega. Solo admite correcciones de estabilización; al cerrar se integra en `main` y de vuelta en `develop`, y se etiqueta en `main`.
- **`hotfix/<version>`:** nace de `main` para una corrección urgente de una versión entregada. Se integra en `main` y `develop`.

Antes de integrar, actualizar la rama destino, comprobar que el cambio funciona y pedir revisión a otro integrante. La revisión puede hacerse en pareja o con un PR; **no se exige un PR**. Para conservar la historia de cada tarea, integrar ramas con `git merge --no-ff`. No hacer `push --force` sobre `main` o `develop`.

## Commits atómicos y convención

Un commit representa **un cambio lógico**: por ejemplo, un requisito, una pantalla o una corrección. Si hay dos cambios independientes, hacer dos commits. El commit debe incluir la prueba o documentación que necesita ese mismo cambio, y dejar el proyecto en un estado coherente.

Usar [Conventional Commits](https://www.conventionalcommits.org/): `tipo(alcance): descripción breve en imperativo`. El alcance es opcional. Tipos habituales:

- `feat`: funcionalidad nueva.
- `fix`: corrección de comportamiento.
- `docs`: documentación.
- `test`: pruebas.
- `refactor`: cambio interno sin alterar comportamiento.
- `chore`: mantenimiento.

Ejemplos: `docs(protocolo): definir ejercicio inicial`, `feat(historial): mostrar sesiones por fecha`, `fix(captura): evitar duplicar una sesión`. En el mensaje o descripción de la tarea, enlazar el issue correspondiente cuando ayude a seguir el motivo del cambio.

## Coordinación entre APK y web

1. Si una tarea afecta ambos repositorios, abrir un issue en cada uno y enlazarlos. Acordar primero el cambio en el [contrato de integración](https://github.com/Luchosqi/movilidad-post-cancer-web/blob/main/docs/contrato-integracion.md).
2. Web mantiene los formatos y ejemplos de asignación y sesión; APK verifica que puede recibir la asignación y que su sesión enviada coincide. Un cambio incompatible requiere nueva versión del contrato y coordinación de las dos integraciones.
3. Revisar que no se versionen credenciales, datos identificables de pacientes, videos clínicos ni bases reales. Las demostraciones usan datos sintéticos.
4. Registrar en los issues los acuerdos de reunión, bloqueos y responsable siguiente. El equipo decide cuándo cortar una rama `release/*` para la entrega del ramo.
