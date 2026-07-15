# Medidor Acústico SGS — PWA

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub, por ejemplo `medidor-acustico-sgs`.
2. Sube **todos los archivos y carpetas** de este paquete, conservando la estructura.
3. En el repositorio abre **Settings > Pages**.
4. En **Build and deployment**, selecciona **Deploy from a branch**.
5. Selecciona la rama `main` y la carpeta `/(root)`; pulsa **Save**.
6. Cuando GitHub muestre la URL publicada, ábrela por HTTPS. En Chrome/Edge usa **Instalar aplicación**; en Android, menú de tres puntos > **Instalar aplicación** o **Añadir a pantalla de inicio**.

## Notas

- Concede permiso de micrófono al iniciar una medición.
- La aplicación requiere conexión la primera vez para cargar Chart.js y SheetJS desde CDN. Después, la página y los recursos propios quedan disponibles sin conexión mediante el service worker; las bibliotecas externas pueden requerir conexión si no estaban ya presentes en la caché del navegador.
- Los niveles son orientativos y no sustituyen un sonómetro homologado.
