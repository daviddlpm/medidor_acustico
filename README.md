# Medidor Acústico SGS — PWA v2.0

## Novedades de esta versión

- **Selección de micrófono**: detecta todas las entradas de audio disponibles (micrófono interno del teléfono y cualquier micrófono externo conectado por USB/USB-C) y permite elegir cuál usar antes de medir o calibrar.
- **Detección en caliente**: si se conecta un micrófono externo mientras la app está abierta, aparece un aviso para seleccionarlo (sin cortar una medición en curso).
- **Calibración por micrófono**: cada micrófono guarda su propio offset de calibración, para no aplicar por error la calibración de un micrófono a otro con sensibilidad distinta. Las calibraciones creadas con la versión anterior se conservan como "heredadas".
- **Gráfica más visible**: mayor altura, escala vertical que se ajusta automáticamente al rango medido, y líneas de referencia con etiqueta numérica que marcan el nivel máximo y mínimo alcanzados durante la medición. Los puntos de máximo y mínimo se resaltan en rojo/verde sobre la curva.
- **Funcionamiento sin conexión real**: Chart.js y SheetJS ahora se sirven desde la propia app (carpeta `vendor/`) en lugar de una CDN externa, por lo que quedan cacheados por el service worker y la app funciona sin internet tras la primera carga.
- **Correcciones de fiabilidad**: se evita iniciar dos mediciones o calibraciones a la vez (pulsaciones dobles), se cierran correctamente el micrófono y el contexto de audio ante errores, se detecta si el navegador no admite grabación de audio, se avisa si la página no se abre por HTTPS, y se elige automáticamente un formato de grabación compatible con el navegador (en iOS/Safari puede diferir de Android/Chrome).
- Los informes (JPG y Excel) incluyen ahora qué micrófono se ha usado en cada medición.

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub, por ejemplo `medidor-acustico-sgs`.
2. Sube **todos los archivos y carpetas** de este paquete (`index.html`, `manifest.webmanifest`, `service-worker.js`, `icons/`, `vendor/`), conservando la estructura.
3. En el repositorio abre **Settings > Pages**.
4. En **Build and deployment**, selecciona **Deploy from a branch**.
5. Selecciona la rama `main` y la carpeta `/(root)`; pulsa **Save**.
6. Cuando GitHub muestre la URL publicada, ábrela por HTTPS. En Chrome/Edge usa **Instalar aplicación**; en Android, menú de tres puntos > **Instalar aplicación** o **Añadir a pantalla de inicio**.

## Uso del micrófono externo (USB-C)

1. Conecte el micrófono/adaptador USB-C al teléfono **antes** de abrir la app (o déjelo conectado y pulse "Detectar micrófonos").
2. Conceda el permiso de micrófono cuando el navegador lo solicite.
3. En la tarjeta "Micrófono", elija el dispositivo deseado en la lista. Los que el sistema identifica como externos se marcan como "(externo, USB-C/USB)".
4. Calibre ese micrófono concreto antes de medir con él: la calibración no se comparte entre micrófonos distintos.

## Notas

- Concede permiso de micrófono al iniciar una medición o calibración.
- Tras la primera visita, la página, sus bibliotecas y los iconos quedan disponibles sin conexión mediante el service worker.
- Los niveles son orientativos y no sustituyen un sonómetro homologado ni una calibración de laboratorio.
- Si cambia de navegador, borra los datos del sitio, o el sistema operativo revoca el permiso de micrófono, tendrá que volver a detectar y calibrar los micrófonos.
