---
date: July 2025
title: "![arc42](images/arc42-logo.png) ERP Taller Diésel VW/MB"
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

## Escenario: Flujo de Compra de Repuesto
1. **Técnico:** Solicita un repuesto vinculado a una **Matrícula**.
2. **Compras:** Genera la orden seleccionando un **Proveedor** del catálogo.
3. **Stock:** Registra la entrada de la pieza y notifica al técnico.
4. **Facturación:** El costo del repuesto se suma automáticamente a la cuenta del vehículo.

---

# 10. Glossary

| Term | Definition |
| :--- | :--- |
| **EIS** | Enterprise Information System - Módulo de información estratégica. |
| **Tecnólogo** | Personal especializado en sistemas complejos (Culatas, Inyección). |
| **Vinculación** | Relación contractual definida en el módulo de RRHH. |
| **Sprinter Exception** | Lógica que limita servicios a vehículos Mercedes-Benz solo para mantenimiento rápido. |

---
