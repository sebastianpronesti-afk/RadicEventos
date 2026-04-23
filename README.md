# Radic Eventos — Sitio web

Sitio estático listo para publicar. No requiere servidor ni base de datos.

---

## 📋 ÍNDICE

1. [Cómo subirlo a internet](#1-cómo-subirlo-a-internet)
2. [Antes de publicar — checklist obligatoria](#2-antes-de-publicar)
3. [Qué editar y dónde](#3-qué-editar-y-dónde)
4. [Activar las secciones desactivadas](#4-secciones-desactivadas)
5. [Para que aparezca en Google](#5-para-que-aparezca-en-google)
6. [Si algo se rompe](#6-si-algo-se-rompe)

---

## 1. Cómo subirlo a internet

### Opción A — Netlify (recomendado, gratis, 5 minutos)

1. Entrá a https://app.netlify.com/drop
2. Arrastrá la carpeta `radic-eventos` completa al recuadro de la web.
3. Listo. Te genera una URL del tipo `random-name-12345.netlify.app`.
4. Para cambiar el nombre: Site settings → Change site name.
5. Para usar tu dominio (ej: `radiceventos.com.ar`): Domain settings → Add custom domain.

### Opción B — Cloudflare Pages (también gratis)

1. Entrá a https://dash.cloudflare.com → Workers & Pages → Create → Pages → Direct Upload.
2. Subí la carpeta y listo.

---

## 2. Antes de publicar

### a) Cambiar los datos de contacto reales

Abrí `index.html` con cualquier editor de texto (Bloc de notas sirve, pero recomiendo VSCode o Notepad++) y buscá y reemplazá:

- `5491112345678` → tu número de WhatsApp real (formato internacional, sin "+" ni espacios)
- `hola@radiceventos.com.ar` → tu email real
- `instagram.com/radiceventos` → tu Instagram real
- `radiceventos.com.ar` → tu dominio real (aparece varias veces en los meta tags)

### b) Activar el formulario de contacto (¡SIN ESTO NO RECIBÍS LOS MENSAJES!)

1. Entrá a https://web3forms.com/
2. Poné tu email y clickeá "Create Access Key" (es gratis, sin cuenta).
3. Te llega un código por mail. Copialo.
4. En `index.html` buscá `YOUR_ACCESS_KEY_HERE` y reemplazalo por ese código.
5. Probá enviando un mensaje de prueba después de publicar.

Web3Forms te permite hasta 250 envíos al mes gratis.

### c) Reemplazar las imágenes

Las imágenes en `/img/` son placeholders generados (fondos oscuros con texto). Reemplazalas por fotos reales **manteniendo los mismos nombres**:

- `hero.jpg` (1920x1080, foto principal del fondo del hero)
- `portfolio-1.jpg` a `portfolio-6.jpg` (1200x900 cada una, fotos de eventos)
- `og-image.jpg` (1200x630, imagen que se muestra al compartir el link en WhatsApp/Facebook)

**Tip:** Antes de subir las fotos, comprimilas en https://squoosh.app — bajan de 4MB a ~300KB sin perder calidad.

### d) Cambiar los números de la sección "Stats"

Los números visibles ("XX años de experiencia", "XX eventos producidos", etc.) son **placeholders**. Buscá `XX` en `index.html` y reemplazá los 4 valores por los reales.

---

## 3. Qué editar y dónde

Toda la web está en un solo archivo: **`index.html`**. Lo abrís con cualquier editor de texto.

Para encontrar rápido cada sección, buscá con Ctrl+F estos íconos. Cada sección importante tiene un comentario grande con instrucciones específicas:

| Buscá esto en el archivo | Te lleva a... |
|---|---|
| `🎯 HERO` | Título principal, subtítulo y botones de la primera pantalla |
| `📊 NÚMEROS` | Cifras de "Años de experiencia", "Eventos producidos", etc. |
| `🖼️ PORTFOLIO` | Galería de eventos (fotos + nombres + categorías) |
| `📞 DATOS DE CONTACTO` | Teléfono, WhatsApp, email, dirección, horarios |
| `📋 TESTIMONIOS` | Sección de reseñas de clientes (desactivada) |
| `🏢 LOGOS DE CLIENTES` | Sección "Confiaron en nosotros" (desactivada) |

### Cómo editar texto sin romper nada

El HTML se ve así:

```
<h1>Eventos diseñados con <em>obsesión por el detalle</em>.</h1>
```

Todo lo que está **entre `>` y `<`** es texto editable. En el ejemplo de arriba, podés cambiar:
- "Eventos diseñados con"
- "obsesión por el detalle"

Lo que **NO tenés que tocar**: cualquier cosa con `<` y `>` alrededor (eso es código).

**Regla de oro**: si algo te parece código, no lo toques. Solo cambiá las palabras visibles.

### Cómo aplicar los cambios al sitio publicado

1. Editás el archivo `index.html` en tu computadora.
2. Volvés a https://app.netlify.com/drop (o tu panel de Netlify) y arrastrás la carpeta de nuevo.
3. Netlify reemplaza la versión vieja por la nueva en segundos.

---

## 4. Secciones desactivadas

Hay dos secciones que dejé "comentadas" en el código (existen pero no se muestran) porque tenían contenido falso:

- **Testimonios** (los nombres de clientes eran inventados)
- **Logos de clientes** (las empresas que aparecían NO son tus clientes)

### Cómo reactivarlas cuando tengas contenido real

Buscá en el archivo el comentario `📋 TESTIMONIOS` o `🏢 LOGOS`. Vas a ver algo así:

```
<!-- /* INICIO_TESTIMONIOS */
    ...mucho código adentro...
/* FIN_TESTIMONIOS */ -->
```

Para activarla:
1. Borrá la línea que dice `<!-- /* INICIO_TESTIMONIOS */`
2. Borrá la línea que dice `/* FIN_TESTIMONIOS */ -->`
3. Reemplazá los textos placeholder ("RESEÑA REAL DEL CLIENTE 1", "Empresa cliente 1", etc.) por los reales.

Es lo mismo para los logos (con sus líneas `INICIO_LOGOS` y `FIN_LOGOS`).

**Importante con los logos**: pedile permiso a la empresa antes de poner su nombre en tu web. Es buena práctica y te evita problemas legales.

---

## 5. Para que aparezca en Google

Una vez publicado el sitio:

1. **Google Search Console** — https://search.google.com/search-console
   - Agregá tu dominio.
   - Verificalo (Netlify te da las opciones).
   - Enviá el sitemap: `https://tudominio.com/sitemap.xml`
2. **Google Business Profile** — https://www.google.com/business/
   - Creá un perfil de empresa local.
   - Esto hace que aparezcas en Google Maps y en búsquedas locales tipo "organizadores de eventos en Buenos Aires".
3. **Tiempo:** Google tarda entre 1 y 4 semanas en indexar un sitio nuevo.

El sitio ya viene preparado con meta tags, Open Graph, Schema.org, sitemap.xml y robots.txt.

---

## 6. Si algo se rompe

Cualquier cambio mal hecho podés deshacerlo volviendo a subir esta carpeta original a Netlify. Te conviene **guardar una copia limpia** antes de empezar a editar.

---

## ¿Querés un panel de administración para editar sin tocar HTML?

Existe la opción de configurar **Decap CMS** (gratis), que te da un panel tipo WordPress en `tudominio.com/admin` donde editás todo desde formularios. Requiere conectar el sitio con GitHub y un setup inicial de unos 30 minutos.

Vale la pena si vas a editar contenido **muy seguido** (semanal). Para cambios cada tanto, editar el HTML directamente y volver a subir es más rápido.
