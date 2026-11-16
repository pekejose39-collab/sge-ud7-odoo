# Proceso de venta completo — AromaSur

Este documento recoge una venta real hecha en Odoo, desde el presupuesto hasta la factura cobrada. Cada paso lo hizo el usuario de su puesto, no el administrador, siguiendo el diseño de permisos de `usuarios/usuarios-grupos-permisos.md`.

**Cliente:** [Nombre del cliente]
**Fecha:** [dd/mm/2026]

## Resumen

| Paso | Usuario | Documento generado | Estado final |
|---|---|---|---|
| 1. Presupuesto | Lucía Martín (comercial) | S000XX | Presupuesto enviado |
| 2. Confirmación | Carlos Calvo (responsable de ventas) | S000XX | Pedido de venta |
| 3. Entrega | Carlos Calvo (responsable de ventas) | WH/OUT/000XX | Hecho |
| 4a. Crear factura | Carlos Calvo (responsable de ventas) | Factura en borrador | Borrador |
| 4b. Publicar factura | Elena Gómez (facturación) | INV/2026/000XX | Publicado |
| 4c. Registrar pago | Elena Gómez (facturación) | PBNK1/2026/000XX | Pagado |
| 5. Estado final | Carlos Calvo (responsable de ventas) | S000XX | Totalmente facturado |

## Paso 1 · Presupuesto (Lucía, comercial)

Lucía creó el presupuesto **S000XX** para **[Nombre del cliente]** en Ventas → Presupuestos → Nuevo. Los datos son:

- **Fecha de validez (vencimiento):** [dd/mm/2026]
- **Plazo de pago:** [30 días]
- **Líneas del presupuesto:**

| Producto | Cantidad | Precio unitario | Descuento | Impuesto |
|---|---|---|---|---|
| Café en grano 100% arábica (250 g) | [10] | 8,90 € | — | 10% |
| Taza de cerámica con logo | [6] | 12,00 € | [10%] | 21% |
| Curso de barista (2 horas) | [1] | 45,00 € | — | 21% |

- **Total (IVA incluido):** [xxx,xx €]

Lo imprimió en PDF desde el botón **Imprimir** (`venta/presupuesto.pdf`), con lo que el estado pasó a **Presupuesto enviado**.

## Paso 2 · Confirmación (Carlos, responsable de ventas)

Carlos, que ve los presupuestos de todo el equipo, abrió **S000XX** y pulsó **Confirmar**. El presupuesto pasó a **Pedido de venta**, y Odoo generó automáticamente la orden de entrega en Inventario.

## Paso 3 · Entrega e inventario (Carlos, responsable de ventas)

Desde el botón **Entrega** del pedido, Carlos abrió la orden **WH/OUT/000XX**. Comprobó que la **cantidad hecha** coincidía con la **cantidad pedida** y pulsó **Validar**. El estado pasó a **Hecho**.

Comprobación del stock (Inventario → Productos):

| Producto | Stock antes | Cantidad entregada | Stock después |
|---|---|---|---|
| Café en grano 100% arábica (250 g) | [60] | [10] | [50] |
| Taza de cerámica con logo | [25] | [6] | [19] |

El curso de barista es un servicio, así que no lleva stock ni aparece en la entrega.

## Paso 4 · Factura y cobro (Carlos y Elena)

Como Elena (facturación) no tiene acceso a Ventas, por el principio de mínimo privilegio, el trabajo se repartió así:

1. **Carlos** pulsó **Crear factura** en el pedido S000XX. Odoo generó la factura en **borrador** con las mismas líneas.
2. **Elena** abrió la factura en Facturación → Clientes → Facturas. Revisó el cliente, las líneas, los impuestos y el plazo de pago, y pulsó **Confirmar**. La factura recibió el número **INV/2026/000XX** y quedó en estado **Publicado**.
3. **Elena** pulsó **Registrar pago** (diario Banco, importe total) y la factura quedó como **Pagado**.

La factura impresa está en `venta/factura.pdf`.

## Paso 5 · Estado final

El pedido **S000XX** aparece como **Totalmente facturado**, y desde él se accede a la entrega (WH/OUT/000XX) y a la factura (INV/2026/000XX). En Ventas → Informes → Ventas se ve la venta incluida en el análisis.

## Capturas

`26` presupuesto de Lucía · `27` pedido confirmado por Carlos · `28` entrega validada · `29` stock después · `30` factura publicada · `31` factura pagada · `32` pedido facturado · `33` análisis de ventas.
