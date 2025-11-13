# ADMINOLT demo

Previsualizacion esttica que replica algunos flujos de SMARTOLT usando datos simulados y almacenamiento local. Sirve para mostrar cmo se veran las ONUs detectadas, configuradas y su historial de autorizaciones.

## Caractersticas principales

- **API local**: `js/api.js` combina los datos del JSON (`api/onus.json`, hosteado en GitHub raw) con las ONUs que se guardan en `localStorage`.
- **ONUs sin configurar**: `index.html` lista solo las pending y solo ofrece el botn Autorizar.
- **Panel configuradas**: `configuraciones.html` agrega filtros avanzados, tabla estilo SMARTOLT y link View que abre `detalle-onu.html`.
- **Detalle de ONU**: `detalle-onu.html` muestra la ficha completa + botones de accin e imgenes mock.
- **Formulario**: `formulario-autorizacion.html` guarda/actualiza la ONU (marcndola como configured y registrando la fecha/usuario).
- **Reportes**: `reportes.html` crea una tabla de autorizaciones con filtros por usuario, bsqueda y rango de fechas.
- **Header reutilizable**: todas las pginas cargan `header.html` dinmicamente con `js/include-header.js`.
- **Estilos modulares**: cada pgina tiene su CSS en `css/<pagina>.css`, que importa `css/main.css`.

## Requisitos

- Navegador moderno con soporte para `fetch` y `localStorage`.
- Servidor esttico (GitHub Pages, Vite preview, `python -m http.server`, etc.).

## Puesta en marcha local

```bash
python -m http.server 8080  # o cualquier servidor esttico
open http://localhost:8080/index.html
```

### Flujo sugerido

1. **ONUs sin configurar**: detecta la lista pendiente y autoriza alguna (botn Autorizar).
2. **Formulario**: completa los datos y envi. Guarda en localStorage y redirige al perfil configurado.
3. **Configuradas**: filtr/orden y us View para abrir la ficha.
4. **Detalle**: revis la ficha + grficos mock.
5. **Reportes**: revis el historial con filtros (bsqueda, usuario, fechas).

## Deploy en GitHub Pages

1. Sub todo el directorio a un repo pblico (`main` branch).
2. En Settings ? Pages, seleccion la branch `main` y la carpeta raz `/`.
3. Esper a que GitHub Pages genere la URL (`https://usuario.github.io/repo`).

> Tip: los enlaces son relativos, por lo que el sitio funciona igual en localhost o Pages.

## Personalizacin

- Actualiz `api/onus.json` o el repo remoto para nuevas ONUs de ejemplo.
- Agreg estilos especficos en `css/<pagina>.css` para cada vista.
- Cambi el header nico editando `header.html`.
- Ajust los scripts en `js/` (por ejemplo, `js/page-reportes.js` para ms columnas o filtros).

## Licencia

Proyecto de demostracin sin licencia explcita. Adptalo libremente para presentaciones internas.


