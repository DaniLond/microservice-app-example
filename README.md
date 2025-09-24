# Proyecto de Despliegue con Pipeline y Microservicios

Este proyecto tiene como objetivo el **despliegue automatizado de microservicios en Azure** utilizando **Docker, Azure Container Apps, Terraform y GitHub Actions**.  
La solución implementa buenas prácticas de arquitectura en la nube, incluyendo:  
- **Contenerización** de microservicios con Docker.  
- **Orquestación y autoscaling** en Azure Container Apps.  
- **Trazabilidad distribuida** con Zipkin.  
- **Resiliencia** mediante el patrón **Circuit Breaker** en `users-api`.  
- **Infraestructura como código (IaC)** gestionada con Terraform.  
- **Integración y despliegue continuo (CI/CD)** con GitHub Actions.  

---

## Documentación del Proyecto

La documentación detallada se encuentra organizada en archivos separados:

- 📌 [Metodología de Trabajo](./metología.md)  
- 🌿 [Estrategia de Branching](./estrategiaBranching.md)  
- 🏗️ [Diagrama de Arquitectura](./arch-img/azure-architecture.drawio.png)  

---

## Repositorio de Infraestructura

El código relacionado con la **infraestructura como código (IaC)** se encuentra en un repositorio separado:  

🔗 [Repositorio de Infraestructura](https://github.com/DaniLond/Microservicio-Infraestructura.git)  
