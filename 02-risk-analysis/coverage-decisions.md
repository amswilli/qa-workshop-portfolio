# Coverage Decisions 

---

## 🚀 Riesgos que se probarán primero

1. **Manipulación de valores y montos en el carrito de compras (R1):** Probar los límites y la validación de montos negativos o precios alterados para evitar transacciones fraudulentas.
2. **Vulnerabilidad de seguridad en operaciones críticas de la API (R2):** Verificar la ausencia de control de acceso en la eliminación o modificación de mascotas (`DELETE /pet/{id}`) e inventarios.
3. **Inconsistencias en el proceso de Registro y Checkout (R3):** Evaluar la validación de datos en el formulario de registro (*Register Now*) para asegurar que la autenticación no bloquee la compra.

---

## 💡 ¿Por qué esos riesgos son prioridad?

* **Protección financiera del negocio:** Un fallo en las validaciones del carrito de compras (R1) genera pérdidas financieras inmediatas e impacta la rentabilidad de JPetStore.
* **Integridad y seguridad de los datos:** Permitir la alteración o borrado del catálogo sin autenticación en la API (R2) expone la operación a ataques externos y pérdida crítica de información.
* **Garantía del flujo transaccional:** Si el registro de usuarios falla o acepta datos inconsistentes (R3), se interrumpe la conversión de ventas, provocando el abandono de la plataforma.

---

## 🚫 Qué se probará menos o quedará fuera por ahora

- **Navegación exhaustiva por categorías del catálogo (R4):** Validación completa de todos los enlaces de categorías y renderizado de productos con baja probabilidad de falla.
- **Manejo de escenarios bordes con productos fuera de stock (R5):** Pruebas profundas sobre la compra de ítems agotados y mensajes de error no controlados en la interfaz visual.

---

## 📜 Justificación de exclusiones

* **(R4):** Aunque los enlaces rotos afectan la experiencia del cliente, tienen menor impacto financiero directo y menor probabilidad de ocurrencia comparados con la validación de pagos o la seguridad.
* **(R5):** Dado que la integración real entre la Web y la API no está confirmada, probar escenarios de agotamiento de stock requiere primero estabilizar las reglas de negocio base del carrito y la API.

