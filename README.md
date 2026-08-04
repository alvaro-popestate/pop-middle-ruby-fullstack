# Prueba Técnica — Desarrollador/a Full Stack Middle (Ruby on Rails)

## Contexto

Una proptech gestiona arriendos de propiedades. Cada mes se debe **liquidar** a los propietarios: calcular cuánto se les debe transferir después de descontar la comisión de gestión y eventuales descuentos manuales.

Tu tarea es construir un **mini-módulo de liquidación manual**.

No evaluamos diseño visual (aunque, dicen por ahí, la portada del libro también vende — si te sobra tiempo y le quieres dar un poco de cariño a la vista, no está de más 😉). Lo que sí evaluamos es criterio de modelado, lógica de negocio, validaciones y clean code.

---

## Qué debes construir

1. **Modelo de datos propio** (tú decides las migraciones y relaciones) para al menos:
   - Propiedad
   - Propietario
   - Liquidación (o Movimiento)
   - Descuento

2. **Una vista de listado** de liquidaciones (aunque sea simple).

3. **Una vista de detalle/formulario** de una liquidación que muestre:
   - Propiedad y propietario asociados
   - Monto del arriendo del período
   - Comisión calculada
   - Descuentos aplicados
   - **Total final a transferir al propietario**

4. **Poder marcar si es la "primera liquidación"** de esa propiedad, y que el cálculo de comisión reaccione a eso.

5. **Poder agregar y quitar descuentos manuales** (glosa + monto), y que el total se recalcule automáticamente.

6. **Guardar los cambios.**

---

## Reglas de negocio

- **Comisión normal:** 7% del monto del arriendo del período.
- **Comisión primera liquidación:** 10% del monto del arriendo del período.
- **Descuentos manuales:** cada uno tiene una glosa (texto libre) y un monto. Se restan del total.
- **Fórmula del total final:**

  ```
  Total = Monto arriendo − Comisión − Σ Descuentos
  ```

---

## Alcance (scope)

Para mantenerlo en 2-4 horas, limita el ejercicio a:

- 1 listado
- 1 vista de detalle/formulario
- 1 acción principal de guardar
- Las 2 reglas de negocio descritas arriba (comisión variable + descuentos)

---

## Non-goals (fuera de alcance, a propósito)

- **Autenticación / autorización** está intencionalmente ausente. Si quieres sugerir una dirección en `NOTES.md`, genial — pero no hace falta implementar nada.
- **La cobertura de tests no es lo que calificamos.** Si agregas tests, son bienvenidos, pero no es un requisito.

---

## Requisitos técnicos

- **Ruby on Rails** (versión a tu elección).
- **Todo debe correr en Docker** (`docker-compose up` debe dejar la app funcionando, incluyendo la base de datos).
- **Base de datos relacional** (PostgreSQL, MySQL, u otra de tu preferencia).
- Puedes usar las gemas que quieras (se agradecerá nombrar en el **`NOTES.md`** porque y para qué utilizaste cada gema).

---

## Uso de Inteligencia Artificial

**Está muy bien usar IA** (Copilot, Cursor, ChatGPT, Claude, etc.) durante todo el desarrollo. De hecho, este ejercicio está pensado para poder resolverse apoyándote en IA — pero también debe ser resoluble de forma manual si lo prefieres.

Si usas IA, debes compartir tus **prompts y una estimación del uso de tokens** en un archivo **`NOTES.md`** aparte. No es para juzgar cuánto la usaste, sino para entender cómo trabajas con estas herramientas.

Además, si te va bien en el ejercicio técnico después habrá una **breve revisión de código en vivo**, donde te pediremos que expliques y, eventualmente, modifiques en caliente partes de tu solución. Nos interesa ver que entiendes lo que construiste, más allá de cómo lo generaste.

---

## Entregables

1. Repositorio (Git) con el código.
2. **README.md** que incluya:
   - Instrucciones para levantar el proyecto con Docker (`docker-compose up` y cualquier paso adicional, como seeds).
   - Cómo acceder a la aplicación una vez levantada.
   - Cualquier decisión de diseño o supuesto que hayas tomado y quieras explicar.
3. **NOTES.md** con tus prompts de IA y una estimación de uso de tokens (si usaste IA).

---

## Qué evaluamos

| Criterio | Qué miramos |
|---|---|
| Modelado de datos | Relaciones correctas, dónde vive la lógica de comisión (modelo vs. vista vs. controller) |
| Lógica de negocio | Cálculo correcto, manejo limpio del caso "primera liquidación" |
| Validaciones | Montos negativos, campos vacíos, casos borde |
| Vista/formulario | Usabilidad básica, el total se refleja bien tras editar |
| Código | Nombres claros, separación de responsabilidades, sin lógica de negocio embebida en la vista |
| Setup con Docker | Que efectivamente levante sin fricción |
| Uso de IA | Calidad de los prompts y criterio al usarlos (vía `NOTES.md`) |
| Revisión en vivo | Capacidad de explicar y modificar su propia solución |

---

¡Éxito!
