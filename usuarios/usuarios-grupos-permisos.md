# Usuarios, grupos y permisos — AromaSur

He diseñado la plantilla aplicando el **principio de mínimo privilegio**: cada persona solo tiene los permisos que necesita su puesto. Si alguien no necesita una aplicación, no tiene acceso a ella.

> Por seguridad, en este documento no aparece ninguna contraseña. Solo se indica el correo de acceso de cada usuario.

## 1. Tipos de usuario en Odoo

- **Interno:** un empleado de la empresa. Entra en el backend de Odoo y usa las aplicaciones según los grupos que tenga asignados. Es el único tipo que ocupa licencia en Enterprise.
- **Portal:** un cliente o proveedor externo. Solo ve el portal web (`/my`), con sus propios presupuestos, pedidos y facturas, y no entra en el backend.
- **Público:** un visitante anónimo del sitio web, sin iniciar sesión. No se crea a mano.

## 2. Usuarios creados

| Usuario | Correo de acceso | Puesto | Tipo | Grupos / privilegios por módulo | Justificación |
|---|---|---|---|---|---|
| [Tu nombre] | admin@tucafe.es | Gerente / administrador | Interno | Ventas: Administrador · Facturación: Administrador · Inventario: Administrador · Ajustes: Administración | Es el responsable del sistema y necesita configurarlo todo. |
| Lucía Martín | lucia.martin@tucafe.es | Comercial | Interno | Ventas: Usuario: solo mostrar documentos propios · Facturación: sin acceso · Inventario: sin acceso · Grupo propio **AromaSur / Comercial junior** | Solo hace sus presupuestos y pedidos. No necesita ver los de sus compañeros ni la contabilidad. |
| Carlos Calvo | carloscalvo@tucafe.es | Responsable de ventas | Interno | Ventas: Administrador · Facturación: sin acceso · Inventario: Usuario | Supervisa al equipo comercial, ve todos los presupuestos y consulta el stock antes de comprometer pedidos. |
| Elena Gómez | elena.gomez@tucafe.es | Administración / Facturación | Interno | Ventas: sin acceso · Facturación: Facturación · Inventario: sin acceso | Emite facturas y registra cobros, pero no crea ni modifica presupuestos de venta. |
| Distribuciones Norte S.L. | compras@distribucionesnorte.es | Cliente (empresa) | Portal | Portal | Consulta online sus presupuestos y facturas, los acepta o firma y los descarga en PDF. No ve nada interno. |

## 3. Grupo propio: «AromaSur / Comercial junior»

Lo he creado en **Ajustes → Usuarios y compañías → Grupos** (con el modo desarrollador activado) para un comercial que empieza: puede vender, pero con más restricciones que un comercial normal.

**Asignado a:** Lucía Martín.

### Grupos heredados

- **Ventas / Usuario: solo mostrar documentos propios.** Al heredarlo, quien tenga este grupo recibe automáticamente todos sus permisos (y los de *Usuario interno*). Así no hay que repetirlos a mano.

### Derechos de acceso sobre modelos

L = Lectura · E = Escritura · C = Creación · B = Eliminación (borrado)

| Nombre del permiso | Modelo | L | E | C | B |
|---|---|:-:|:-:|:-:|:-:|
| AromaSur junior – contactos | Contacto (`res.partner`) | ✅ | ✅ | ✅ | ❌ |
| AromaSur junior – productos | Plantilla de producto (`product.template`) | ✅ | ❌ | ❌ | ❌ |
| AromaSur junior – pedidos de venta | Pedido de venta (`sale.order`) | ✅ | ✅ | ✅ | ❌ |

**Por qué:** puede consultar y crear clientes y presupuestos, que es su trabajo, pero **no puede borrar** clientes ni pedidos, para evitar perder información. Tampoco puede modificar los productos ni sus precios: el catálogo solo lo toca el responsable.

> **Nota:** en Odoo los permisos **se suman**. Si un usuario tiene otro grupo que sí permite borrar, podrá borrar. Por eso al comercial junior solo le he asignado este grupo (que ya hereda Ventas / Usuario) y no otros grupos de ventas con más permisos.

## 4. Comprobación de permisos

He iniciado sesión con cada usuario (en una ventana privada del navegador) para comprobar que los permisos funcionan:

- **Lucía (comercial junior):** ve el menú Ventas, pero **no** ve Facturación ni Ajustes. En Presupuestos solo aparecen los suyos. Al intentar borrar un cliente, Odoo muestra un error de acceso. *(capturas `20` a `22`)*
- **Carlos (responsable de ventas):** ve los presupuestos de **todos** los comerciales y tiene acceso a la configuración de Ventas. No ve Facturación. *(captura `23`)*
- **Elena (facturación):** ve el menú Facturación, crea facturas y registra pagos, pero **no** ve el menú Ventas. *(captura `24`)*
- **Cliente portal:** al entrar solo ve la página «Mi cuenta» con sus documentos. *(captura `25`)*
