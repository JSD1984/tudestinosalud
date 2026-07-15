# 🤖 Receta para publicar guías en Destino Salud (para la IA)

Guía para que un agente de IA publique nuevas guías en **Destino Salud** copiando el estilo del sitio.
El sitio es **HTML estático**: no hay build. Cada cambio en la rama `main` se publica solo en Vercel en 1–2 minutos.

- **Publisher AdSense:** `ca-pub-6858538787372520` (el mismo de tus otros sitios).
- **Dominio (placeholder):** `www.destinosalud.com` → cámbialo por el real cuando lo tengas.

---

## Publicar una guía = 3 pasos

### Paso 1 — crear el artículo
Copia **exactamente** la estructura de cualquier fichero de `articulos/` (por ejemplo `injerto-capilar-turquia-guia.html`) y guarda el nuevo como `articulos/{slug}.html`. Cambia solo:
- `<title>`, `<meta name="description">`, `og:title`
- El `kicker`, el `<h1>`, la fecha y el tiempo de lectura del `article-hero`
- El color de la portada (`article-cover`) y el emoji `.ico`
- El cuerpo dentro de `<div class="prose">`

> Mantén el bloque AdSense in-article, la newsletter, el footer y el `<script>` del menú tal cual.

### Paso 2 — añadir la tarjeta en las listas
Añade el bloque de **tarjeta** (ver abajo) al principio de `<div class="grid">` en:
1. `blog.html` (siempre)
2. La página de su sección: `cirugia-estetica.html`, `turismo-dental.html` o `destinos-bienestar.html`
3. (Opcional) La rejilla de `index.html`, y quita la tarjeta más antigua para que queden 4.

### Paso 3 — añadir la URL al sitemap
Edita `sitemap.xml` y añade:
```xml
<url><loc>https://www.destinosalud.com/articulos/{slug}.html</loc><lastmod>AAAA-MM-DD</lastmod><changefreq>monthly</changefreq><priority>0.7</priority></url>
```

---

## Convenciones
- **slug:** minúsculas, con guiones, sin acentos ni espacios. Ej.: `bichectomia-en-el-extranjero`.
- **Fecha:** formato `D de mes de AAAA` en el artículo (ej.: `15 de julio de 2026`) y `AAAA-MM-DD` en el sitemap.
- **Categorías y su clase de degradado + emoji de miniatura:**
  - Cirugía estética → `thumb g3` · ✨
  - Injerto capilar → `thumb g1` · 💈
  - Turismo dental → `thumb g2` · 🦷
  - Destinos → `thumb g6` · ✈️
  - Bienestar → `thumb g5` · 🧖
  - Guía esencial → `thumb g4` · 🧭

---

## ✍️ Estilo de escritura (OBLIGATORIO)
El lector es una **persona normal** que está pensando en viajar para operarse o mejorar su salud, y tiene miedo a equivocarse. Escribe para ayudarle a decidir, no para venderle nada.

Fórmula de cada guía:
1. Primera frase que entra directa en la **situación real** del lector (busca en Google, le llegan ofertas por WhatsApp…).
2. Explicación sencilla y honesta del tema.
3. **Riesgos y letra pequeña** que nadie le cuenta.
4. Pasos concretos / lista de comprobación.
5. Una idea práctica accionable (`callout`).
6. Cierre con el **aviso médico** (`disclaimer`), siempre.

Tono: cercano, adulto, tranquilizador, sin humo. Frases cortas.
**Prohibido:** promesas médicas, "el mejor precio garantizado", urgencia falsa, presentarse como clínica o vendedor.

## Estructura del cuerpo (dentro de `<div class="prose">`)
- Varios `<p>` cortos para abrir.
- `<h2>` por sección.
- `<ul><li>…</li></ul>` con la idea clave en `<strong>`.
- `<blockquote>` para una frase potente.
- `<div class="callout"><b>Idea práctica:</b> …</div>` para el consejo accionable.
- Un bloque `<div class="ad-slot">…</div>` con el `<ins class="adsbygoogle">` a media guía.
- **Siempre** cerrar con `<div class="disclaimer">…</div>` (aviso de que no es consejo médico).

---

## 🧩 Bloque de TARJETA (para las listas)
```html
<a class="card" href="articulos/{slug}.html">
  <div class="thumb g3"><span>{Categoría}</span><span class="ico">✨</span></div>
  <div class="body">
    <div class="meta">{Categoría} · {D mes AAAA} · {N} min</div>
    <h3>{Titular}</h3>
    <p>{Resumen de una frase}</p>
    <span class="more">Leer guía →</span>
  </div>
</a>
```

## 📢 AdSense
- El `<script>` de AdSense y el `<meta name="google-adsense-account">` ya están en el `<head>` de todas las páginas.
- El `<ins class="adsbygoogle">` de dentro de los artículos usa `data-ad-slot="0000000000"` como placeholder: sustitúyelo por el ID real de tu bloque de anuncios cuando lo crees en el panel de AdSense.
- `ads.txt` en la raíz ya declara tu publisher. No lo toques.
