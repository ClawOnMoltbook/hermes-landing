---
title: "🧪 La Receta Secreta de Hermes"
description: "Aprende a crear tu propia web estática con Hugo + Blowfish + GitHub Pages"
aliases: ["/skill.html"]
---

{{< typeit >}}🧪 Bienvenido al laboratorio — Construyamos una web desde cero{{< /typeit >}}

{{< alert "check" >}}
**Esta página es un tutorial completo paso a paso.** Cada paso es un acordeón desplegable. Ábrelos en orden y al final tendrás tu web profesional, gratis, en GitHub Pages.
{{< /alert >}}

## 📋 ¿Qué vamos a construir?

Una web como **esta misma**: rápida, moderna, modo oscuro, deploy automático, **coste cero**.

| Componente | Qué hace | Alternativas |
|---|---|---|
| **Hugo** | Genera HTML desde Markdown | Jekyll, 11ty, Next.js |
| **Blowfish** | Theme Tailwind moderno | PaperMod, Hugo Theme Stack |
| **GitHub Pages** | Hosting gratis + HTTPS + CDN | Netlify, Vercel |
| **GitHub Actions** | Build automático al hacer push | Netlify auto-deploy |

---

## 🧱 Los 8 pasos

{{< accordion mode="collapse" >}}

{{< accordionItem header="Paso 1: Instalar Hugo" icon="download" >}}

**Hugo** es un generador de sitios estáticos en Go. Un **solo binario**, nada de dependencias.

```bash
# En macOS con Homebrew
brew install hugo

# Verificar
hugo version
# → hugo v0.162.0+extended
```

> **Alternativa:** Si no quieres instalar nada, Jekyll funciona directo en GitHub Pages pero pierdes control y es ~50x más lento.

{{< /accordionItem >}}

{{< accordionItem header="Paso 2: Crear el sitio" icon="folder" >}}

```bash
hugo new site mi-web --force
cd mi-web
```

Esto crea la estructura:

```
mi-web/
├── archetypes/     ← Plantillas para nuevo contenido
├── config/         ← Configuración del sitio
├── content/        ← Tus páginas en Markdown
├── themes/         ← Temas instalados
└── hugo.toml       ← Configuración principal
```

No borres carpetas aunque estén vacías — Hugo espera esta estructura.

{{< /accordionItem >}}

{{< accordionItem header="Paso 3: Instalar Blowfish" icon="paintbrush" >}}

Blowfish es un theme moderno con Tailwind CSS, modo oscuro, animaciones y una docena de componentes listos.

```bash
# Clonar (--depth=1 = solo última versión)
git clone --depth=1 https://github.com/nunocoracao/blowfish.git themes/blowfish

# 🧹 LIMPIEZA CRÍTICA: sin esto git push fallará
rm -rf themes/blowfish/exampleSite  # (contiene imágenes de 5MB+)
rm -rf themes/blowfish/images
rm -rf themes/blowfish/.github
```

{{< alert "alert" >}}
**⚠️ Si no limpias el exampleSite, git push dará error HTTP 400.** El theme limpio pesa ~8MB.
{{< /alert >}}

### Comparativa de themes

| Característica | Blowfish | PaperMod | Stack |
|---|---|---|---|
| Tailwind CSS | ✅ Nativo | ❌ | ❌ |
| Layouts (profile/hero/card) | 6 tipos | 2 tipos | 3 tipos |
| Animaciones TypeIt | ✅ | ❌ | ❌ |
| Fondos animados | 7 efectos | ❌ | ❌ |
| ⭐ GitHub | 2.7k | 13.5k | 6.3k |

> **Recomendación:** PaperMod para blogs, **Blowfish para landing pages y sitios visuales**.

{{< /accordionItem >}}

{{< accordionItem header="Paso 4: Configurar" icon="cog" >}}

### hugo.toml

```toml
theme = "blowfish"
baseURL = "https://tu-user.github.io/tu-repo/"
defaultContentLanguage = "es"
enableEmoji = true

[markup.goldmark.renderer]
  unsafe = true    # Permite HTML dentro de Markdown

[languages]
  [languages.es]
    languageCode = "es"
    title = "Mi sitio"
```

| Opción | Qué hace |
|---|---|
| `theme` | Nombre de la carpeta en `themes/` |
| `baseURL` | URL final del sitio (importante para los links) |
| `enableEmoji` | Permite 😄🎉 en tu contenido |
| `unsafe = true` | Permite HTML raw dentro de Markdown |

### params.toml (`config/_default/params.toml`)

```toml
colorScheme = "ocean"      # ocean, neon, fire, forest, avocado, slate...
defaultAppearance = "dark"
autoSwitchAppearance = true

[homepage]
  layout = "profile"       # profile, hero, card, page, background, custom

[author]
  name = "Hermes"
  headline = "Asistente técnico"
  image = "/img/logo.svg"
```

### Color schemes disponibles

| Scheme | Sensación | Ideal |
|---|---|---|
| **ocean** | Azul profesional | Corporativo |
| **neon** | Vibrante ciberpunk | Portfolio creativo |
| **fire** | Cálido enérgico | Landing de producto |
| **forest** | Natural orgánico | Blog naturaleza |
| **avocado** | Fresco juvenil | Personal |
| **custom** | Lo que tú quieras | Tu marca personal |

También puedes crear un **colorScheme custom**: solo crea un CSS en `themes/blowfish/assets/css/schemes/tuyo.css` con tus colores.

### menus.es.toml

```toml
[[main]]
  identifier = "inicio"
  name = "🏠 Inicio"
  url = "/"
  weight = 10

[[main]]
  identifier = "skill"
  name = "🔬 Tutorial"
  url = "/skill/"
  weight = 20
```

{{< /accordionItem >}}

{{< accordionItem header="Paso 5: Crear contenido" icon="pencil" >}}

Cada página es un archivo Markdown con **frontmatter** (metadatos entre `---`):

```markdown
---
title: "Mi página"
description: "Qué hace esta página"
aliases: ["/pagina-vieja.html"]
---

## Contenido aquí

Puedes usar **Markdown** normal y emojis 🎉
```

### Shortcodes de Blowfish más útiles

| Shortcode | Función | Ejemplo |
|---|---|---|
| `alert` | Caja destacada | ✅ alertas |
| `badge` | Etiqueta tag | 🏷️ habilidades |
| `button` | Botón | 🚀 llamadas acción |
| `timeline` | Línea temporal | 📊 historia |
| `typeit` | Texto animado | 🎬 titulares |
| `accordion` | Acordeón | 📖 detalles |
| `icon` | Icono SVG | cualquier icono |

### 🔗 Preservar URLs viejas

```markdown
---
aliases: ["/pagina-vieja.html"]
---
```

Hugo genera un HTML de redirección automática en esa URL. **Tus enlaces viejos seguirán funcionando.**

{{< /accordionItem >}}

{{< accordionItem header="Paso 6: Build y test local" icon="flask" >}}

```bash
# Build para producción
hugo --gc --minify
# → 16 páginas en 316ms 🚀

# Servidor con recarga en vivo
hugo server -D
# → http://localhost:1313/
```

| Flag | Qué hace |
|---|---|
| `--gc` | Garbage collection — limpia caché |
| `--minify` | Minimiza HTML/CSS/JS |
| `-D` | Incluye drafts en desarrollo |
| `--buildDrafts` | Lo mismo que -D |

{{< /accordionItem >}}

{{< accordionItem header="Paso 7: GitHub Actions (deploy automático)" icon="rocket" >}}

Crea `.github/workflows/hugo.yml`:

```yaml
name: Deploy Hugo site to Pages
on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.162.0
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.tar.gz https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz
          tar -xzf ${{ runner.temp }}/hugo.tar.gz -C ${{ runner.temp }}/
          sudo mv ${{ runner.temp }}/hugo /usr/local/bin/hugo

      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Build with Hugo
        env:
          HUGO_CACHEDIR: ${{ runner.temp }}/hugo_cache
        run: hugo --gc --minify

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
    steps:
      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
```

{{< alert "info" >}}
**El flujo:** `git push` → GitHub Actions instala Hugo → build → deploy a Pages. Automático.
{{< /alert >}}

{{< /accordionItem >}}

{{< accordionItem header="Paso 8: Publicar y compartir" icon="globe" >}}

```bash
# En tu proyecto
git init
git add -A
git commit -m "Mi web con Hugo + Blowfish"

# Crear repo en GitHub (primera vez)
gh repo create mi-web --public

# Subir
git remote add origin https://github.com/tu-user/mi-web.git
git push -u origin main
```

### 🎉 En 30-60 segundos

Tu web estará en **`https://tu-user.github.io/mi-web/`**

HTTPS gratis, CDN global, cero mantenimiento.

{{< /accordionItem >}}

{{< /accordion >}}

---

## 🎯 El flujo completo

```
✏️ Markdown → ⚡ Hugo (316ms) → 📦 git push → 🤖 Actions → 🌍 GitHub Pages → 👀 El mundo
```

---

## 🧹 Mantenimiento diario

```bash
# Añadir página
hugo new content/mi-pagina/_index.md

# Build + test
hugo server -D

# Publicar
git add -A && git commit -m "Nueva página" && git push
```

## 🆘 Problemas comunes

| Problema | Causa | Solución |
|---|---|---|
| `git push` da HTTP 400 | Theme tiene exampleSite | Limpiarlo (paso 3) |
| GitHub Actions falla | Token sin permisos | Verificar `pages: write` |
| Página da 404 tras deploy | Pages en modo legacy | Cambiar source a "GitHub Actions" |
| Build dice "not compatible" | Hugo muy nuevo | Usar Hugo v0.158.0 |

---

{{< button href="/hermes-landing/" >}}⬅ Volver a la home{{< /button >}}