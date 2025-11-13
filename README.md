# ADMINOLT demo

Previsualizacion estática que replica algunos flujos de SMARTOLT usando datos simulados y almacenamiento local. Sirve para mostrar cómo se verían las ONUs detectadas, configuradas y su historial de autorizaciones.

## Características principales

- **API local**: `js/api.js` combina los datos del JSON (`api/onus.json`, hosteado en GitHub raw) con las ONUs que se guardan en `localStorage`.
- **ONUs sin configurar**: `Onus-Sinconfigurar.html` lista solo las pending y solo ofrece el botón Autorizar.
- **Panel configuradas**: `configuraciones.html` agrega filtros avanzados, tabla estilo SMARTOLT y link “View” que abre `detalle-onu.html`.
- **Detalle de ONU**: `detalle-onu.html` muestra la ficha completa + botones de acción e imágenes mock.
- **Formulario**: `formulario-autorizacion.html` guarda/actualiza la ONU (marcándola como configured y registrando la fecha/usuario).
- **Reportes**: `reportes.html` crea una tabla de autorizaciones con filtros por usuario, búsqueda y rango de fechas.
- **Header reutilizable**: todas las páginas cargan `header.html` dinámicamente con `js/include-header.js`.
- **Estilos modulares**: cada página tiene su CSS en `css/<pagina>.css`, que importa `css/main.css`.

## Requisitos

- Navegador moderno con soporte para `fetch` y `localStorage`.
- Servidor estático (GitHub Pages, Vite preview, `python -m http.server`, etc.).

## Puesta en marcha local

```bash
python -m http.server 8080  # o cualquier servidor estático
open http://localhost:8080/Onus-Sinconfigurar.html
```

### Flujo sugerido

1. **ONUs sin configurar**: detecta la lista pendiente y autoriza alguna (botón Autorizar).
2. **Formulario**: completa los datos y enviá. Guarda en localStorage y redirige al perfil configurado.
3. **Configuradas**: filtrá/ordená y usá “View” para abrir la ficha.
4. **Detalle**: revisá la ficha + gráficos mock.
5. **Reportes**: revisá el historial con filtros (búsqueda, usuario, fechas).

## Deploy en GitHub Pages

1. Subí todo el directorio a un repo público (`main` branch).
2. En Settings ? Pages, seleccioná la branch `main` y la carpeta raíz `/`.
3. Esperá a que GitHub Pages genere la URL (`https://usuario.github.io/repo`).

> Tip: los enlaces son relativos, por lo que el sitio funciona igual en localhost o Pages.

## Personalización

- Actualizá `api/onus.json` o el repo remoto para nuevas ONUs de ejemplo.
- Agregá estilos específicos en `css/<pagina>.css` para cada vista.
- Cambiá el header único editando `header.html`.
- Ajustá los scripts en `js/` (por ejemplo, `js/page-reportes.js` para más columnas o filtros).

## Licencia

Proyecto de demostración sin licencia explícita. Adáptalo libremente para presentaciones internas.
