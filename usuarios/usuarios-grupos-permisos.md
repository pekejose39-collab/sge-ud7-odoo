# Usuarios, grupos y permisos

## Usuarios creados

| Usuario | Correo (login) | Puesto | Aplicaciones con acceso |
|---|---|---|---|
| Administrador/a | admin@aromasur.example | Gerencia | Todas (Administrador/a) |
| Carlos Ruiz | ventas@aromasur.example | Comercial | Ventas, Contactos |
| Ana López | contabilidad@aromasur.example | Administración | Facturación, Contactos |
| Pedro Gómez | almacen@aromasur.example | Almacén | Inventario |

## Permisos por usuario

| Usuario | Ventas | Facturación | Inventario | Ajustes |
|---|---|---|---|---|
| Administrador/a | Administrador | Administrador | Administrador | Sí |
| Carlos Ruiz | Usuario: solo sus documentos | — | — | No |
| Ana López | — | Facturación | — | No |
| Pedro Gómez | — | — | Usuario | No |

## Justificación

- **Principio de mínimo privilegio:** cada persona solo ve lo que necesita para su trabajo.
- El comercial solo ve **sus propios** presupuestos y pedidos.
- Administración puede facturar, pero no modificar la configuración de ventas.
- Solo gerencia tiene acceso a *Ajustes*.

## Comprobación

_Describe cómo has comprobado los permisos (por ejemplo, iniciando sesión con
cada usuario) y enlaza las capturas:_

- ![Usuarios](../capturas/usuarios-lista.png)
