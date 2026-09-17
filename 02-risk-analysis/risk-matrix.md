# Risk Matrix

---

| ID | Riesgo | Impacto | Probabilidad | Nivel | Justificación |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R1** | El usuario podría modificar el total a pagar o agregar ítems con precio/cantidad negativa en el carrito sin que el sistema lo valide[cite: 1]. | Alto | Alta | **Crítico** | Afecta directamente los ingresos de la empresa y genera pérdidas financieras inmediatas en las transacciones[cite: 1]. |
| **R2** | La API permite la modificación o eliminación de datos de mascotas (`DELETE /pet/{id}`) y pedidos sin requerir autenticación ni API Key obligatoria[cite: 1]. | Alto | Alta | **Crítico** | Cualquier usuario o atacante externo podría borrar el catálogo o alterar inventarios reales afectando la operación del negocio[cite: 1]. |
| **R3** | El sistema podría permitir la creación de cuentas con datos duplicados o incompletos durante el registro (*Register Now*) congelando el flujo de checkout[cite: 1]. | Alto | Media | **Alto** | Provoca la pérdida imprevista de ventas al no permitir a los usuarios completar el proceso de autenticación y pago[cite: 1]. |
| **R4** | Los enlaces de navegación entre categorías de mascotas (*peces, perros, reptiles*) redirigen a páginas rotas o muestran listas de productos totalmente vacías[cite: 1]. | Medio | Baja | **Medio** | Deteriora la credibilidad de la plataforma y bloquea el flujo de exploración del catálogo[cite: 1]. |
| **R5** | La interfaz web permite agregar al carrito productos cuyo stock está agotado (*Out of Stock*), arrojando un error no controlado al intentar pagar[cite: 1]. | Medio | Media | **Medio** | Impacta negativamente la experiencia del usuario (UX) y genera inconsistencia en la gestión de inventario[cite: 1]. |