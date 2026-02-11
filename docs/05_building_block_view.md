![arc42](images/arc42-logo.png)

---
Fecha: Julio 2025
Titulo: "ERP Taller Diésel VW/MB"
---


# 5. Building Block View

![Diagrama de Contenedores](<images/Diagrama de Contenedores Nivel 2 - C2.png>)

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
