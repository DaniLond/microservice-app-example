# Metodología Seleccionada: **Kanban**

Para el desarrollo y despliegue de este proyecto se utilizó la **metodología Kanban**, la cual nos permitió organizar las tareas de forma visual y progresiva, dividiéndolas en columnas representativas del flujo de trabajo:

* **To Do**: Tareas pendientes por ejecutar.
* **In Progress**: Tareas en desarrollo.
* **Done**: Tareas finalizadas y verificadas.

El uso de Kanban nos permitió:

* Tener **visibilidad completa** del estado de cada tarea.
* Garantizar un **flujo continuo de trabajo** evitando bloqueos.
* **Priorizar entregables** de manera flexible según la necesidad del equipo.
* Adaptarnos a cambios en tiempo real sin perder el control del proceso.

---

## Pasos Implementados en el Proyecto

A continuación, se describe el flujo de trabajo seguido para lograr el despliegue de los microservicios con pipelines:

### 1. Preparación del código base

1. Clonar el repositorio.
2. Agregar el `Dockerfile` en todos los microservicios.
3. En el **frontend**:

   * Crear `nginx.config`.
   * Modificar los archivos de rutas (incluyendo **Zipkin** y **Auth**).
4. En **users-api**:

   * Modificar `application.properties` para leer la variable de entorno `ZIPKIN_URL`.
   * Implementar el patrón **Circuit Breaker**.

---

### 2. Contenerización inicial

5. Crear el **docker-compose.yml**.
6. Probar la correcta ejecución del `docker-compose`.
7. Subir la configuración a un repositorio.

---

### 3. Infraestructura base

8. Crear la carpeta `infra_base/`.

9. Configurar un **Blob Storage** para almacenar el estado.

10. En `infra_base/` crear `main.tf` para definir:

    * Azure Container Apps.

    * Repositorio de imágenes.

11. Inicializar el backend con `terraform init`.

12. Desplegar la infraestructura base.

13. Subir la configuración a un repositorio.

---

### 4. Configuración de repositorios y secretos

14. En el repositorio de desarrollo definir secretos:

* `ACR_LOGIN_SERVER`
* `ADMIN_USERNAME`
* `ADMIN_PASSWORD`
* Token, auto deploy y credenciales adicionales.

---

### 5. Automatización con Pipelines

15. Crear los pipelines:

* `build-and-push.yml`
* `redeploy-container-apps.yml`

16. Ejecutar el pipeline

---

### 6. Infraestructura de aplicaciones

17. En la carpeta `infra_base/`, crear una subcarpeta `apps/`.
18. Definir los archivos necesarios para las **apps**.
19. Inicializar con `terraform init` cambiando el `key` del archivo de `infra_base` a `apps`.
20. Crear el pipeline `build-and-push.yml`.
21. En el pipeline de infraestructura, configurar los secretos:

* Key del Storage Account.
* Token.
* Credenciales de acceso.

---

## Conclusión

La metodología **Kanban** nos permitió mantener un control visual y adaptable de todas las fases del despliegue, desde la preparación del código, contenerización, configuración de la infraestructura en Azure, hasta la automatización mediante pipelines.

Este flujo garantiza:

* **Escalabilidad** en la infraestructura.
* **Automatización** en la entrega continua (CI/CD).
* **Resiliencia** en los microservicios mediante patrones como **Circuit Breaker**.
