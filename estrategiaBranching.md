# Estrategia de Branching

En nuestro proyecto utilizamos la estrategia **GitHub Flow**, ya que se adapta a nuestras necesidades de desarrollo y despliegue continuo con microservicios e infraestructura.

---

## Implementación en el Proyecto

### Repositorio de Desarrollo

* **`master` (rama principal):**
  Contiene la versión estable del proyecto de microservicios.

* **Ramas de características (`feature/*`):**
  Se crean para cada nueva funcionalidad o ajuste específico. Ejemplos:

  * `feature/CircuitBreaker` → Implementación del patrón Circuit Breaker.
  * `feature/docker` → Configuración de `Dockerfile` en los microservicios.
  * `feature/pipelineForRedeploy` → Pipeline para redeploy.
  * `feature/pipelinePushBuild` → Pipeline para build y push de imágenes.

**Flujo de trabajo:**

1. Crear una rama `feature/*` desde `master`.
2. Desarrollar la funcionalidad o cambio requerido.
3. Crear un Pull Request (PR) hacia `master`.
4. Revisar, aprobar y mergear el PR.
5. Desplegar desde la rama `master`.

---

### Repositorio de Infraestructura

* **`main` (rama principal):**
  Contiene la configuración estable de la infraestructura como código (Terraform y pipelines).

* **Ramas auxiliares:**

  * `pipelineBuildPush` → Configuración y pruebas de los pipelines de construcción y despliegue.

**Flujo de trabajo:**

1. Crear ramas específicas para nuevos ajustes en infraestructura.
2. Validar y probar los cambios.
3. Generar un PR hacia `main`.
4. Una vez aprobado, mergear a `main` y aplicar cambios en el entorno.

---

