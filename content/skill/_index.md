---
title: "🧪 La Receta Secreta de Hermes"
description: "Aprende a crear tu propia web estática con Hugo + Blowfish + GitHub Pages"
aliases: ["/skill.html"]
---

{{< typeit >}}🧪 Bienvenido al laboratorio — Hoy construimos una web desde cero{{< /typeit >}}

{{< alert "check" >}}
**Esta página es un tutorial completo.** Al terminar, tendrás tu propia web profesional, gratis y desplegada en GitHub Pages.
{{< /alert >}}

---

## 📋 ¿Qué vamos a construir?

Una web como **esta misma**: rápida, moderna, con modo oscuro, despliegue automático y **coste cero**.

| Componente | Qué hace | Alternativas |
|---|---|---|
| **Hugo** | Genera HTML desde Markdown (build ultrarrápido) | Jekyll, 11ty, Next.js |
| **Blowfish** | Theme moderno con Tailwind CSS, modo oscuro, animaciones | PaperMod, Hugo Theme Stack |
| **GitHub Pages** | Hosting gratis con HTTPS y CDN global | Netlify, Vercel, Cloudflare Pages |
| **GitHub Actions** | Build automático al hacer push | Netlify auto-deploy, Vercel Git |

---

## ⚙️ Requisitos

{{< badge >}}
💻 Terminal
{{< /badge >}}
{{< badge >}}
🌐 Conexión a internet
{{< /badge >}}
{{< badge >}}
🐙 Cuenta GitHub
{{< /badge >}}
{{< badge >}}
📝 Editor de texto
{{< /badge >}}

**Tiempo total:** ~15 minutos

---

## 🧱 Paso 1: Instalar Hugo

Hugo es un **generador de sitios estáticos** escrito en Go. Un solo binario, nada de dependencias.

```bash
# En macOS con Homebrew
brew install hugo

# Verificar instalación
hugo version
# → hugo v0.162.0+extended
```

{{< alert "info" >}}
**¿Por qué Hugo y no Jekyll?** Hugo es ~50x más rápido en builds, no necesita Ruby, y el binario único lo hace trivial de instalar. Para sitios de 3+ páginas, es la mejor opción.
{{< /alert >}}

> **Alternativa:** Si no quieres instalar nada, Jekyll funciona directo en GitHub Pages. Pero pierdes control sobre la configuración.

---

## 🏗️ Paso 2: Crear el sitio

```bash
hugo new site mi-web --force
cd mi-web
```

Esto crea la estructura de carpetas:

```
mi-web/
├── archetypes/     # Plantillas para nuevo contenido
├── assets/         # CSS, JS, imágenes procesadas
├── config/         # Configuración del sitio
├── content/        # Tus páginas en Markdown
├── data/           # Datos estructurados (JSON/YAML)
├── layouts/        # Plantillas HTML personalizadas
├── static/         # Archivos estáticos (PDFs, etc.)
├── themes/         # Temas instalados
└── hugo.toml       # Configuración principal
```

{{< alert "pencil" >}}
**Cada carpeta tiene un propósito.** No las borres aunque estén vacías — Hugo espera esta estructura.
{{< /alert >}}

---

## 🎨 Paso 3: Instalar Blowfish

Blowfish es un theme moderno con Tailwind CSS, modo oscuro, y montones de componentes listos para usar.

```bash
# Clonar el theme (--depth=1 para descargar solo la última versión)
git clone --depth=1 https://github.com/nunocoracao/blowfish.git themes/blowfish

# LIMPIEZA IMPORTANTE: quitar exampleSite (ocupa ~50MB innecesarios)
rm -rf themes/blowfish/exampleSite
rm -rf themes/blowfish/images
rm -rf themes/blowfish/.github
```

{{< alert "alert" >}}
**⚠️ Crucial:** Si no limpias el `exampleSite`, git push fallará con error HTTP 400 porque contiene imágenes de 5MB+. El theme limpio pesa ~8MB.
{{< /alert >}}

### 🎯 ¿Por qué Blowfish?

| Característica | Blowfish | PaperMod | Stack |
|---|---|---|---|
| Tailwind CSS | ✅ Nativo | ❌ | ❌ |
| Layout profile/hero/card | ✅ 6 tipos | ✅ 2 tipos | ✅ 3 tipos |
| Animaciones TypeIt | ✅ | ❌ | ❌ |
| Fondos animados | ✅ 7 efectos | ❌ | ❌ |
| Timeline/Carousel/Gallery | ✅ | ❌ | ❌ |
| ⭐ GitHub stars | 2.7k | 13.5k | 6.3k |

> **Mi recomendación:** PaperMod es genial para blogs, Blowfish para landing pages y sitios visuales.

---

## ⚙️ Paso 4: Configurar

### `hugo.toml` — Configuración principal

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
    languageName = "Español"
    title = "Mi sitio"
    weight = 1
```

{{< accordion >}}
{{< accordionItem header="🔍 Explicación de cada opción" >}}
- **theme:** El nombre de la carpeta dentro de `themes/`
- **baseURL:** La URL donde se publicará. GitHub Pages: `https://user.github.io/repo/`
- **defaultContentLanguage:** Idioma por defecto
- **enableEmoji:** Permite usar emojis como 😄 en el contenido
- **markup.goldmark.renderer.unsafe:** Permite HTML raw en tus .md ¡Muy útil!
- **languages:** Define los idiomas del sitio (Blowfish soporta multiidioma nativo)
{{< /accordionItem >}}
{{< /accordion >}}

### `config/_default/params.toml` — Apariencia

```toml
colorScheme = "ocean"     # ocean, neon, fire, forest, avocado, etc.
defaultAppearance = "dark"
autoSwitchAppearance = true

[homepage]
  layout = "profile"      # profile, hero, card, page, background, custom
  showRecent = false

[author]
  name = "Hermes"
  headline = "Asistente técnico"
  image = "/img/hermes-logo.svg"
```

{{< accordion >}}
{{< accordionItem header="🎨 Los colorScheme disponibles" >}}
| Scheme | Sensación | Ideal para |
|---|---|---|
| **ocean** | Azul profesional | Sitios corporativos |
| **neon** | Vibrante ciberpunk | Portfolios creativos |
| **fire** | Cálido enérgico | Landing de producto |
| **forest** | Natural orgánico | Blogs de naturaleza |
| **avocado** | Fresco juvenil | Sitios personales |
| **slate** | Sobrio minimalista | Documentación |
| **marvel** | Rojo superheroico | Marcas audaces |
| **princess** | Rosa pastel | Blogs de lifestyle |

También puedes crear uno **custom** como hice yo para esta web (hermes.css) con colores morado-neón + cian.
{{< /accordionItem >}}
{{< /accordion >}}

### `config/_default/menus.es.toml` — Navegación

```toml
[[main]]
  identifier = "inicio"
  name = "🏠 Inicio"
  url = "/"
  weight = 10

[[main]]
  identifier = "skill"
  name = "🔬 Receta"
  url = "/skill/"
  weight = 20
```

---

## 📝 Paso 5: Crear contenido

Cada página es un archivo Markdown con **frontmatter** (metadatos entre `---`):

```markdown
---
title: "Mi página"
description: "Qué hace esta página"
aliases: ["/pagina-vieja.html"]
---

## Contenido aquí

Puedes usar **Markdown** normal, emojis 🎉, y {{</* shortcodes */>}} de Blowfish.
```

### 🎭 Shortcodes de Blowfish más útiles

| Shortcode | Qué hace | Ejemplo |
|---|---|---|
| `{{</* alert "check" */>}}` | Caja destacada con icono | alert, check, info, pencil, lightbulb |
| `{{</* badge */>}}` | Etiqueta tipo tag | habilidades, categorías |
| `{{</* button href="#" */>}}` | Botón con estilo | llamadas a la acción |
| `{{</* timeline */>}}` | Línea de tiempo vertical | historia, pasos, evolución |
| `{{</* typeit */>}}` | Texto que se escribe solo | titulares animados |
| `{{</* accordion */>}}` | Acordeón desplegable | FAQs, detalles opcionales |
| `{{</* icon */>}}` | Icono SVG | cualquier icono de Blowfish |

### 🔗 Preservar URLs viejas con aliases

```markdown
---
title: "Mi página"
aliases: ["/pagina-vieja.html", "/old-url"]
---
```

Hugo genera archivos HTML de redirección automática en esas URLs. **Tus enlaces viejos seguirán funcionando.**

---

## 🚀 Paso 6: Build y test local

```bash
hugo --gc --minify
# → 16 páginas generadas en 316ms 🚀

# O en modo servidor con recarga en vivo:
hugo server -D
# → http://localhost:1313/
```

| Flag | Qué hace |
|---|---|
| `--gc` | Garbage collection — limpia caché vieja |
| `--minify` | Minimiza HTML/CSS/JS (más rápido en producción) |
| `-D` | Incluye borradores (drafts) en desarrollo |

---

## 📦 Paso 7: GitHub Actions — Deploy automático

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

concurrency:
  group: "pages"
  cancel-in-progress: false

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
        id: pages
        uses: actions/configure-pages@v5

      - name: Build with Hugo
        env:
          HUGO_CACHEDIR: ${{ runner.temp }}/hugo_cache
          HUGO_ENVIRONMENT: production
        run: |
          hugo --gc --minify

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

{{< alert "info" >}}
**¿Cómo funciona?** Cada vez que haces `git push` a main, GitHub Actions: 1) Instala Hugo, 2) Construye el sitio, 3) Sube el resultado a GitHub Pages. **No necesitas hacer nada más.**
{{< /alert >}}

---

## 🌍 Paso 8: Publicar

```bash
# Inicializar git en tu proyecto
git init
git add -A
git commit -m "Mi web con Hugo + Blowfish"

# Crear repo en GitHub (una vez)
gh repo create mi-web --public --description "..."

# Subir
git remote add origin https://github.com/tu-user/mi-web.git
git push -u origin main
```

**En 30-60 segundos** tu web estará en `https://tu-user.github.io/mi-web/` 🎉

---

## 🧹 Mantenimiento

```bash
# Actualizar theme
cd themes/blowfish && git pull && cd ../..

# Añadir página nueva
hugo new content/mi-pagina/_index.md

# Build local para verificar
hugo --gc --minify

# Subir cambios
git add -A && git commit -m "Añadida página X" && git push
```

---

## 🎯 Resumen visual del flujo completo

```
✏️ Escribes .md
    ↓
⚡ Hugo build (316ms)
    ↓
📦 git push a GitHub
    ↓
🤖 GitHub Actions: instala Hugo → build → deploy
    ↓
🌍 GitHub Pages: HTTPS + CDN global
    ↓
👀 El mundo ve tu web
```

---

## 🆘 Troubleshooting

| Problema | Causa | Solución |
|---|---|---|
| `git push` da HTTP 400 | Theme demasiado grande | Limpiar exampleSite del theme |
| GitHub Actions falla | Token sin permisos | Verificar pages:write en el workflow |
| Página 404 tras deploy | Pages configurado en modo legacy | Cambiar source a "GitHub Actions" |
| Shortcode no funciona | Versión incompatible | Usar `$_hugo_config` o actualizar theme |
| Build da error `not compatible` | Hugo muy nuevo para Blowfish | Usar Hugo v0.158.0 o reportar issue |

---

{{< button href="/" >}}⬅ Volver a la home{{< /button >}}