---
title: "⚔️ HTML plano vs Hugo vs Jekyll"
description: "Cómo hacemos la web ahora y qué alternativas tenemos"
aliases: ["/html-vs-hugo-vs-jekyll.html"]
---

Los tres son estáticos y funcionan en GitHub Pages gratis. Pero cada uno tiene su personalidad.

---

## 📄 HTML plano — Ahora mismo

{{< alert "check" >}}
▸ **AHORA MISMO** — Escribimos HTML directamente.
{{< /alert >}}

```html
<!-- index.html -->
<html>
  <head><title>Hermes</title></head>
  <body><h1>Hola</h1></body>
</html>
```

| ✅ Pros | ❌ Contras |
|---|---|
| Sin dependencias — solo un editor | Escala fatal |
| Sin build, sin esperas | +3 páginas = infierno |
| Lo que escribes es lo que se ve | Cambiar menú = editar todas |

---

## ⚡ Hugo — El que estamos usando ahora

**Go — Single binary.** Escribes en Markdown y usas plantillas. Hugo genera el HTML.

```go
// layouts/_default/baseof.html
<html>
  <head><title>{{ .Title }}</title></head>
  <body>{{ block "main" }}{{ .Content }}{{ end }}</body>
</html>
```

| ✅ Pros | ❌ Contras |
|---|---|
| Rapidísimo (<1ms/página) | Curva de aprendizaje |
| Markdown + temas | Sistema de templates |
| Multilenguaje integrado | |

**Características:**
- Escribes en Markdown (como en Obsidian)
- Plantillas reutilizables — cambias 1 cosa, se actualiza todo
- Build ultrarrápido
- Temas pre-hechos (cientos gratis)
- Blog con posts, fechas, categorías nativo
- Multilenguaje integrado
- No necesita Ruby ni Python — solo el binario de Hugo

---

## 💎 Jekyll — Nativo de GitHub Pages

**Ruby.** Escribes en Markdown con Liquid templates. Creado por Tom Preston-Werner (co-fundador de GitHub).

```markdown
---
title: "Hola mundo"
date: 2026-05-27
tags: [bienvenida]
---

## Mi primer post

Esto está escrito en **Markdown**.
```

| ✅ Pros | ❌ Contras |
|---|---|
| GitHub lo compila solo | Lento en builds grandes |
| Sin instalar nada local | Ruby pesado de instalar |
| El más veterano (2010) | |

**Características:**
- Escribes en Markdown
- Integración nativa con GitHub Pages
- No necesitas build local — GitHub lo hace por ti
- Posts con fecha automática
- Categorías, tags, RSS incluidos
- Temas oficiales mantenidos por GitHub

---

## 📊 Comparativa completa

| Característica | 📄 HTML plano | ⚡ Hugo | 💎 Jekyll |
|---|---|---|---|
| **Escribes en** | HTML puro | Markdown + Go templates | Markdown + Liquid |
| **Instalación** | Nada | Binario Hugo | Ruby + Bundler |
| **Build local** | No necesita | Milisegundos | Segundos |
| **GitHub lo compila** | ✅ Directo | ⚠️ Con action extra | ✅ Nativo |
| **Reutilizar menú** | ❌ Copiar/pegar | ✅ Plantillas | ✅ Plantillas |
| **Blog / Posts** | ❌ A mano | ✅ Nativo | ✅ Nativo |
| **Multilenguaje** | ❌ Duplicas HTML | ✅ Integrado | ⚠️ Con plugin |
| **Temas** | ❌ No existen | ✅ Cientos | ✅ Cientos |
| **Velocidad build** | ✅ Instantáneo | ✅ <1ms/página | ⚠️ 1-5s/10 páginas |
| **Curva aprendizaje** | ✅ Cero | ⚠️ Media | ⚠️ Media |
| **Ideal para** | 1-3 páginas simples | Docs, blogs grandes | Blogs personales |

---

## 🏗️ Arquitectura de cada uno

**📄 HTML plano:**
```
✏️ Escribes .html → 📦 git push → 🌍 GitHub Pages → 👀 Navegador
```

**⚡ Hugo:**
```
✏️ Escribes .md → ⚡ Hugo build → 📄 Genera .html → 📦 git push → 🌍 GitHub Pages
```

**💎 Jekyll:**
```
✏️ Escribes .md → 📦 git push → 💎 GitHub compila Jekyll → 🌍 GitHub Pages
```
*No necesitas instalar nada. GitHub ejecuta Jekyll por ti.*

---

## 🤔 ¿Cuál usar?

| Situación | Recomendación |
|---|---|
| Landing de 1 página | ✅ HTML plano |
| Blog personal pequeño | 💎 Jekyll |
| Documentación técnica grande | ⚡ Hugo |
| Portfolio visual | ⚡ Hugo (Blowfish, PaperMod) |
| Sin ganas de instalar nada local | 💎 Jekyll |

💡 **Dato:** El sitio de Hermes Agent (hermes-agent.nousresearch.com) usa Hugo. También la documentación de Google, Kubernetes y Docker.