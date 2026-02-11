---
date: July 2025
title: "![arc42](images/arc42-logo.png) ERP Taller Diésel VW/MB"
---


# 10. Glossary

A continuación se definen los términos técnicos y de dominio fundamentales para el desarrollo y mantenimiento del ERP Taller Diésel.

| Término | Definición |
| :--- | :--- |
| **API Gateway** | Punto de entrada único que actúa como fachada para los módulos independientes (RRHH, Nómina, Compras), gestionando la autenticación y el enrutamiento. |
| **DTO (Data Transfer Object)** | Objeto utilizado para transportar datos entre los módulos (ej. de Compras a Stock) sin exponer la lógica de las entidades de base de datos. |
| **EIS (Executive Information System)** | Componente de inteligencia de negocios que consolida datos de facturación y costos para la toma de decisiones gerenciales. |
| **Entidad de Dominio** | Objeto de software que representa un concepto de negocio con identidad propia, como un `Proveedor` o un `Vehículo`. |
| **Inyección Common Rail** | Sistema de inyección directa de combustible a alta presión; el ERP debe catalogar repuestos específicos (sensores, inyectores) para esta tecnología. |
| **Módulo Desacoplado** | Componente de software diseñado para funcionar con mínima dependencia de otros, permitiendo que `Nómina` sea modificado sin afectar a `RRHH`. |
| **Norma VW 505.01 / 507.00** | Especificaciones técnicas de lubricantes para motores diésel Volkswagen; el sistema de inventario debe validar estos estándares. |
| **OM Series (Mercedes-Benz)** | Designación de motores diésel de Mercedes-Benz (ej. OM 651); el sistema debe filtrar el despiece de Sprinter bajo estos códigos. |
| **Persistence Layer** | Capa de la arquitectura encargada de almacenar y recuperar datos de la base de datos PostgreSQL. |
| **Rol de Usuario (RBAC)** | Control de acceso basado en roles que define qué acciones puede realizar un Ingeniero, Tecnólogo o Administrativo en el sistema. |
| **SKU (Stock Keeping Unit)** | Código identificador único para cada repuesto en el inventario, fundamental para el rastreo de piezas diésel. |
| **TDI (Turbocharged Direct Injection)** | Marca registrada de motores diésel de Volkswagen; el ERP utiliza este tag para agrupar procedimientos de servicio y repuestos. |
| **Vinculación Contractual** | Objeto lógico en el módulo de RRHH que define la relación legal del empleado, independiente de la liquidación económica en Nómina. |

---
