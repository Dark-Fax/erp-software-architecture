# ![arc42](docs/images/arc42-logo.png)

---
date: July 2025
title: "ERP Taller Diésel VW/MB"
---

# 1. Introduction and Goals

## Requirements Overview
El sistema ERP está diseñado para la gestión técnica y administrativa de un taller especializado en motores diésel (Volkswagen y Mercedes-Benz Sprinter).
* **Módulos Independientes:** Separación estricta entre RRHH (contratación) y Nómina (pagos).
* **Gestión de Compras:** Flujo transaccional separado del directorio de Proveedores.
* **Control por Matrícula:** Trazabilidad total de repuestos y mano de obra por vehículo.

## Quality Goals
* **Modularidad:** Los módulos deben ser independientes para facilitar el mantenimiento.
* **Precisión:** Control exacto de stock de repuestos críticos (inyectores, turbos).
* **Seguridad:** Acceso restringido según el cargo (Ingeniero, Tecnólogo, Técnico).

## Stakeholders

| Role/Name | Contact | Expectations |
| :--- | :--- | :--- |
| **Jefe de Taller** | Ing. Jefe | Supervisar diagnósticos y aprobar compras de repuestos. |
| **Administrador** | Contabilidad | Gestionar nómina, facturación y pagos a proveedores. |
| **Técnico/Tecnólogo** | Operarios | Registrar reparaciones y solicitar repuestos por matrícula. |

---

# 2. Architecture Constraints
* **Backend:** Desarrollo en **Java 21** con **Spring Boot 3**.
* **Frontend:** Aplicación SPA con **React** y TypeScript.
* **Base de Datos:** **PostgreSQL** para garantizar integridad referencial.
* **Documentación:** Uso del estándar **arc42**.

---

# 3. Context and Scope

## Business Context
El sistema centraliza las operaciones del taller, interactuando con proveedores externos y clientes finales.

![Diagrama de Contexto](<docs/images/Diagrama de Contexto Nivel 1 - C1.png>)


---

# 5. Building Block View

![Diagrama de Contenedores](<docs/images/Diagrama de Contenedores Nivel 2 - C2.png>)

## Whitebox Overall System
El sistema se estructura en componentes desacoplados para cumplir con la independencia de módulos solicitada.

### Módulo RRHH (Black Box)
* **Responsabilidad:** Gestionar la vinculación laboral, tipos de contrato (Fijo, Obra) y perfiles (Tecnólogo en Inyección, Técnico en Suspensión).
* **Interfaces:** Provee datos de empleados al módulo de Nómina.

### Módulo Nómina (Black Box)
* **Responsabilidad:** Procesar pagos, deducciones y bonificaciones según el cargo y desempeño.
* **Interfaces:** Consume datos de RRHH y reportes de horas del Taller.

### Módulo Compras (Black Box)
* **Responsabilidad:** Ejecutar órdenes de compra y seguimiento de pedidos.
* **Interfaces:** Consulta el catálogo del Módulo de Proveedores y actualiza el Módulo de Stock.



---

# 6. Runtime View

![Diagrama de Secuencia](<docs/images/Diagrama de Secuencia.png>)

## Escenario: Flujo de Compra de Repuesto
1. **Técnico:** Solicita un repuesto vinculado a una **Matrícula**.
2. **Compras:** Genera la orden seleccionando un **Proveedor** del catálogo.
3. **Stock:** Registra la entrada de la pieza y notifica al técnico.
4. **Facturación:** El costo del repuesto se suma automáticamente a la cuenta del vehículo.

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
