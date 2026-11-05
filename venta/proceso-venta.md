# Proceso de venta

Ciclo completo realizado en Odoo: **presupuesto → pedido de venta → entrega → factura**.

## 1. Datos de la venta

| Campo | Valor |
|---|---|
| Cliente | Cafetería La Esquina |
| Comercial | Carlos Ruiz |
| Fecha | _dd/mm/aaaa_ |
| Nº presupuesto | _S00001_ |
| Nº factura | _INV/2026/00001_ |

| Producto | Cantidad | Precio unitario | IVA |
|---|---|---|---|
| CAF-004 Café en grano Blend Hostelería 1 kg | 10 | 19,50 € | 10 % |
| ACC-003 Filtros de papel (100 uds) | 5 | 6,50 € | 21 % |

## 2. Pasos seguidos

1. **Crear presupuesto:** *Ventas → Pedidos → Presupuestos → Nuevo*. Se elige el cliente y se añaden las líneas.
2. **Enviar / imprimir presupuesto:** *Imprimir → Presupuesto / Pedido* → [presupuesto.pdf](presupuesto.pdf).
3. **Confirmar:** el presupuesto pasa a **pedido de venta**.
4. **Entrega:** se valida el albarán desde el botón *Entrega* (si Inventario está instalado).
5. **Crear factura:** *Crear factura → Factura normal* y *Confirmar*.
6. **Imprimir factura:** → [factura.pdf](factura.pdf).
7. **Registrar pago:** *Registrar pago* (estado: *Pagado*).

## 3. Capturas

- ![Presupuesto](../capturas/venta-presupuesto.png)
- ![Pedido confirmado](../capturas/venta-pedido.png)
- ![Factura](../capturas/venta-factura.png)

## 4. Conclusión

_Comenta brevemente qué te ha parecido el flujo y qué ventajas aporta a la empresa._
