# Radar de Redes · Ticketeras Perú

Dashboard de Joinnus para el equipo de Redes Sociales: compara seguidores, social selling y campañas de **Joinnus, Teleticket, Ticketmaster Perú, Vaope, Passline Perú y Blicket** en Instagram, TikTok, Facebook y YouTube.

## Archivos
- `index.html` → el dashboard (trae un snapshot de datos incluido, funciona solo).
- `data/cuentas.csv` → seguidores por ticketera y red (una fila por cuenta y fecha).
- `data/posts.csv` → posts con likes, comentarios y texto (para campañas y social selling).
- `assets/` → imágenes de campañas propias (ej. Sorteo Octubre) y la librería para exportar a Excel.

## Exportar a Excel
En la sección **Tabla de datos**: botón **Descargar Excel** (un .xlsx con 6 hojas: Cuentas, Historial, Posts, Social selling, Campañas, Comparador) o un **CSV** por tabla (separador `;`, se abre directo en Excel en español). Las descargas respetan los filtros activos. El comparador y social selling también tienen su propio botón de exportar.

## Publicarlo en GitHub Pages (5 min, sin código)
1. En GitHub, dentro de la organización **Marketing-joinnus**, crea un repositorio nuevo: `dashboard-redes` (público).
2. Clic en **Add file → Upload files** y arrastra `index.html`, `README.md` y las carpetas `data` y `assets`. Clic en **Commit changes**.
3. Ve a **Settings → Pages** → en *Branch* elige `main` y carpeta `/ (root)` → **Save**.
4. En 1–2 minutos queda en: `https://marketing-joinnus.github.io/dashboard-redes/`

## Mantenerlo actualizado ("en vivo") con Google Sheets
1. Crea un Google Sheet con dos pestañas: **cuentas** y **posts**. Importa en cada una el CSV de la carpeta `data` (Archivo → Importar).
2. Archivo → Compartir → **Publicar en la web** → elige la pestaña *cuentas* → formato **CSV** → Publicar. Copia el link. Repite con *posts*.
3. En `index.html`, busca `CONFIG` (arriba del código) y pega los links:
   ```
   SHEET_CUENTAS_CSV: "https://docs.google.com/spreadsheets/d/e/.../pub?gid=0&single=true&output=csv",
   SHEET_POSTS_CSV:   "https://docs.google.com/spreadsheets/d/e/.../pub?gid=123&single=true&output=csv",
   ```
   (En GitHub: abre el archivo → ícono del lápiz → pegar → Commit.)
4. Listo: cada vez que alguien abre el dashboard (y cada 5 min) lee el Sheet. El indicador arriba dirá **"En vivo · Google Sheet"**.

### Rutina sugerida (cada lunes, ~15 min)
- En **cuentas**: agrega filas nuevas con la fecha del día y los seguidores de cada perfil (no borres las anteriores → así se arma la curva de **Evolución**).
- En **posts**: pega los posts destacados de la semana (fecha, ticketera, red, url, tipo, likes, comentarios, texto). Las **campañas** se detectan solas por palabras clave y hashtags.
- Para sumar otra ticketera, solo agrega sus filas: aparece automáticamente en filtros y gráficos.

## Columnas
**cuentas:** `fecha (AAAA-MM-DD), ticketera, red (Instagram/TikTok/Facebook/YouTube), usuario, url, seguidores, publicaciones, me_gusta_totales, hablando_de_esto`
**posts:** `fecha, ticketera, red, url, tipo (Post/Reel/Video), likes, comentarios, texto, imagen` (opcional: `vistas`)

> Campañas propias (como el **Sorteo Octubre** de Joinnus) se pueden registrar a mano: deja *likes* y *comentarios* vacíos, pon en *red* el canal (ej. "Web / multicanal") y en *imagen* la ruta de la pieza (`assets/...`). Aparecen en Campañas detectadas y en el feed, sin afectar las medianas de interacción.

## Fuente de los datos iniciales
Datos públicos visibles en cada perfil al 26–27 de octubre de 2026. Instagram muestra seguidores redondeados (ej. 556K). No incluye datos privados ni de pauta.
