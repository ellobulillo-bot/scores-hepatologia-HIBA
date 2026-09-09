# Scores en Hepatología

Herramienta de consulta de puntajes pronósticos y diagnósticos para los fellows de la Sección Hepatología del Hospital Italiano de Buenos Aires.

Es una aplicación web instalable (PWA): una vez publicada, se agrega al escritorio de la computadora o a la pantalla de inicio del celular y funciona sin conexión. Todo el cálculo ocurre en el navegador; no se envía ni se guarda ningún dato.

## Contenido

| Archivo | Qué es |
|---|---|
| `index.html` | La aplicación completa (HTML, CSS y JavaScript en un solo archivo) |
| `manifest.webmanifest` | Metadatos de instalación: nombre, colores, íconos |
| `sw.js` | Service worker: guarda la aplicación en caché para que funcione sin conexión |
| `icons/` | Logo en SVG y sus versiones PNG (64, 180, 192, 512 y maskable 512) |
| `.nojekyll` | Evita que GitHub Pages procese los archivos con Jekyll |

## Publicar en GitHub Pages

1. Crear un repositorio nuevo, por ejemplo `scores-hepatologia`.
2. Subir todos los archivos de esta carpeta a la raíz del repositorio (`index.html` tiene que quedar en la raíz, no dentro de una subcarpeta).
3. Ir a **Settings → Pages**. En *Source* elegir **Deploy from a branch**, rama `main`, carpeta `/ (root)`. Guardar.
4. A los pocos minutos queda publicada en `https://<usuario>.github.io/scores-hepatologia/`. Esa es la dirección para repartir.

Todas las rutas del proyecto son relativas, así que funciona igual en la raíz del dominio o en un subdirectorio.

> El repositorio puede ser privado, pero GitHub Pages en repositorios privados requiere plan pago. Con un repositorio público la página queda accesible para cualquiera que tenga el enlace.

## Instalar en un dispositivo

**Computadora (Chrome o Edge).** Abrir la página y usar el ícono de instalación en la barra de direcciones, o el botón *Instalar en este dispositivo* que aparece arriba a la derecha. Queda como aplicación con su propia ventana y con acceso directo en el escritorio.

**Android (Chrome).** Menú ⋮ → *Instalar aplicación* o *Agregar a pantalla principal*.

**iPhone y iPad (Safari).** Botón Compartir → *Agregar a inicio*. En iOS la instalación sólo funciona desde Safari, no desde Chrome.

Una vez instalada, la aplicación abre sin conexión.

## Actualizar

Reemplazar `index.html` y subir el cambio. Para que los dispositivos que ya la tienen instalada tomen la versión nueva, subir también el número de versión en `sw.js`:

```js
const CACHE = "scores-hep-v2";   // v1 → v2
```

Sin ese cambio el service worker sigue sirviendo la copia vieja desde la caché.

## Alcance

Reproduce fórmulas publicadas con fines de referencia y enseñanza. No sustituye el juicio clínico ni las calculadoras oficiales de asignación de órganos: para MELD 3.0 con fines de lista de espera rige la calculadora del organismo de procuración correspondiente.

Cada puntaje se presenta en tres bloques separados: el valor calculado exacto, los rangos de clasificación, y las estimaciones publicadas con la cita de la que provienen.
