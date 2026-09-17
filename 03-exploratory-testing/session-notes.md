# Sesión 1

## Charter
**Misión:** Explorar el comportamiento del carrito de compras ingresando valores límite (cantidades 0, valores negativos, números con caracteres especiales o volúmenes masivos de ítems) y manipulando el flujo de actualización de totales, con el propósito de descubrir vulnerabilidades de cálculo de precios, fallas en la lógica de negocio o transacciones fraudulentas antes de pasar al checkout.

## ÁREAS
* **Sistema:** Aplicación Web JPetStore.
* **Entorno / URL:** https://petstore.octoperf.com/actions/Catalog.action
* **Navegador / SO:** Google Chrome / Windows 11.

## INICIO
* **Fecha y Hora de Inicio:** 2026-09-16 10:00 AM
* **Duración propuesta:** 45 minutos.
* **Hora de Finalización:** 2026-09-16 10:45 AM

## TESTER
Wilson Williams

## DESGLOSE DE TAREAS
* **Análisis de la sesión / Diseño:** 10% (Definición de casos límite a ingresar).
* **Ejecución de Pruebas:** 70% (Exploración interactiva en la web).
* **Reporte de Bugs / Documentación:** 20% (Captura de evidencias y registro de notas).

## ARCHIVOS DE DATOS
* **Cantidades Límite Probadas:** `-1`, `-99`, `0`, `999999`, `ABC`, `1.5`, `<script>alert(1)</script>`.
* **Productos Seleccionados:** `EST-1` (FI-SW-01 - Angelfish), `EST-6` (K9-BD-01 - Bulldog).

## NOTAS DE PRUEBA
* **Navegación y Selección de Productos:** Se ingresó al catálogo desde la página principal y se agregaron dos productos al carrito de compras sin estar autenticado.
* **Validación de Entradas en la Columna *Quantity*:**
  * Al ingresar la cantidad `-5` en el campo *Quantity* del producto y presionar *"Update Cart"*, el sistema aceptó el número negativo y recalculó el *Sub Total* borrando el articulo seleccionado.
  * Al ingresar la cantidad `0`, el producto tambien desaparece de la lista.
  * Al ingresar decimales (`1.5`), la aplicación los convierte a `1` sin arrojar una alerta clara al usuario.
* **Persistencia al Autenticar:** Al hacer clic en *"Proceed to Checkout"* sin sesión activa, la aplicación solicita login. Tras registrar un nuevo usuario e iniciar sesión, los ítems agregados previamente continuaban en el carrito.

## LISTA DE RIESGOS
* **Pérdida Financiera por Inyección de Valores Negativos:** Un cliente astuto podría ingresar valores negativos para compensar el costo de otros productos y pagar un monto inferior o cercano a cero.
* **Manejo de Inventario:** Permitir cantidades decimales o cero podría causar descuadres al descontar stock en la base de datos.

## DEFECTOS (BUGS)
* **BUG-001:** Inconsistencia visual al ingresar cantidad `0`: el producto se elimina de la tabla pero su subtotal queda congelado en `$0.00`.

## INCIDENTES (ISSUES)
* **Duda de Negocio:** El sistema debería vaciar automáticamente el carrito cuando la sesión permanece inactiva por más de 30 minutos.
* **Falta de Integración Confirmada:** No es posible verificar si las modificaciones de stock en la Web afectan en tiempo real los contadores visibles en la API REST de Swagger.