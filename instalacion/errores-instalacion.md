# Errores encontrados durante la instalación

> Rellena una fila por cada problema real que te haya surgido. Abajo tienes
> ejemplos típicos: **borra los que no te hayan pasado**.

| # | Error / síntoma | Causa | Solución aplicada |
|---|---|---|---|
| 1 | `port is already allocated` al levantar el contenedor de Odoo | El puerto 8069 lo estaba usando otro servicio | Cambiar el mapeo a `8070:8069` en `docker-compose.yml` |
| 2 | `could not connect to server: Connection refused` (PostgreSQL) | Odoo arrancó antes que la base de datos | Añadir `depends_on: db` y reiniciar con `docker compose up -d` |
| 3 | No se puede crear la base de datos desde el navegador | Contraseña maestra incorrecta | Revisar `admin_passwd` en `odoo.conf` |
| 4 | Pantalla en inglés | Idioma no cargado | *Ajustes → Traducciones → Añadir idioma → Español* |
| 5 | | | |

## Notas

- Versión de Odoo: _17 / 18 (indica la tuya)_
- Método de instalación: _Docker / instalador Windows / Ubuntu / Odoo.sh_
- Capturas relacionadas: [capturas/](../capturas/)
