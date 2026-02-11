# erp-software-architecture
Este será el repositorio dedicado para el proyecto de Arquitectura de Software como integrante del grupo A22 "Concesionario de Autos" 

# ERP Taller Diésel - Especialista Volkswagen & Sprinter

Este proyecto consiste en el desarrollo de un **Sistema de Planificación de Recursos Empresariales (ERP)** diseñado a medida para un taller mecánico de alta complejidad. El enfoque principal es la línea Diésel de **Volkswagen** (Amarok, Transporter, Vento TDI) y servicios de mantenimiento rápido para **Mercedes-Benz Sprinter**.

## Módulos del Sistema
El software está construido bajo una arquitectura modular desacoplada:
* **RRHH:** Gestión de contratos y perfiles técnicos (Ingenieros, Tecnólogos, Técnicos).
* **Nómina:** Motor de pagos independiente de la vinculación legal.
* **Compras:** Gestión transaccional de pedidos de repuestos.
* **Proveedores:** Directorio y catálogo de proveedores especializados VW/MB.
* **Inventario & Stock:** Control de repuestos críticos y lubricantes bajo norma.
* **Facturación & Clientes:** Gestión de citas por matrícula y cobros.

---

## Documentación de Arquitectura (arc42)

La arquitectura del sistema está documentada siguiendo el estándar **arc42**. Puedes consultar el [Documento Completo aquí](./arc42-template-EN.md) o navegar por las secciones específicas a continuación:

### Secciones Detalladas
1.  **[Introducción y Objetivos](./docs/01_introduction_and_goals.md):** Visión general y metas de calidad.
2.  **[Restricciones de Arquitectura](./docs/02_architecture_constraints.md):** Decisiones técnicas y stack tecnológico (Java/React).
3.  **[Contexto y Alcance](./docs/03_system_scope_and_context.md):** Diagrama de contexto (C1) y fronteras del sistema.
4.  **[Vista de Bloques](./docs/05_building_block_view.md):** Estructura técnica de los módulos y Diagrama de Contenedores (C2).
5.  **[Vista de Comportamiento](./docs/06_runtime_view.md):** Flujos de ejecución (ej. Proceso de Compra).
6.  **[Glosario Técnico](./docs/10_glossary.md):** Definiciones de dominio diésel y términos de software.

---

## Stack Tecnológico
* **Backend:** Java 21 + Spring Boot 3
* **Frontend:** React + TypeScript
* **Database:** PostgreSQL
* **Metodología:** Scrum (Gestión en Jira)

## Instalación y Desarrollo
*(Próximamente: Instrucciones para `docker-compose up` y configuración del entorno local)*

---
**Desarrollado para el sector automotriz Diésel de alto rendimiento.**
