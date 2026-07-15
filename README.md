# Destino Salud

Sitio web de contenidos sobre **turismo médico, estético y de bienestar**. HTML/CSS estático, sin build, monetizado con Google AdSense y pensado para que una IA vaya publicando guías.

> El nombre "Destino Salud" y el dominio `destinosalud.com` son una propuesta inicial. Para cambiarlos, ver más abajo.

## Estructura
```
index.html               Portada (destacado + rejilla + lateral)
blog.html                Todas las guías
cirugia-estetica.html    Sección
turismo-dental.html      Sección
destinos-bienestar.html  Sección
sobre.html               Sobre nosotros
contacto.html            Contacto
privacidad.html          Política de privacidad + cookies/AdSense
articulos/*.html         Las guías (6 de arranque)
css/estilo.css           Toda la hoja de estilos
ads.txt                  Declaración de AdSense
robots.txt / sitemap.xml SEO
vercel.json              Config de despliegue (estático, cleanUrls)
RECETA-AGENTE.md         Cómo debe la IA añadir nuevas guías
```

## Ver en local
Abre `index.html` en el navegador, o levanta un servidor estático:
```bash
python3 -m http.server 8000    # y abre http://localhost:8000
```

## Publicar (Vercel + GitHub)
1. Crea un repo en GitHub y sube esta carpeta.
2. En Vercel: *Add New Project* → importa el repo. Como es estático, no necesita build; `vercel.json` ya lo deja listo.
3. Añade tu dominio en Vercel (Settings → Domains).
4. Cada `git push` a `main` republica el sitio en 1–2 minutos.

## Conectar Google AdSense
El código de AdSense (`ca-pub-6858538787372520`, tu mismo publisher) ya está integrado en todas las páginas y en `ads.txt`. Para activarlo en este sitio:
1. Entra en tu cuenta de AdSense → **Sites** → **Add site** e introduce el dominio final.
2. AdSense revisará el sitio (necesita contenido real y las páginas de *Sobre*, *Contacto* y *Privacidad*: ya están hechas).
3. Cuando cree tus bloques de anuncios, copia el `data-ad-slot` real y sustituye el placeholder `0000000000` de los `<ins class="adsbygoogle">` dentro de `articulos/`.

## Cambiar el nombre / dominio
Buscar y reemplazar en todo el proyecto:
- `Destino Salud` / `Destino<span>Salud</span>` → tu marca
- `destinosalud.com` → tu dominio
- (Opcional) el logo SVG y los colores en `css/estilo.css` (`--teal`, `--amber`, `--navy`).
