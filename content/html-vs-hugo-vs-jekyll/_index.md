---
title: "⚔️ HTML plano vs Hugo vs Jekyll"
description: "Cómo hacemos la web ahora y qué alternativas tenemos"
aliases: ["/html-vs-hugo-vs-jekyll.html"]
---

{{< typeit >}}Los tres son estáticos... cada uno con su personalidad {{< /typeit >}}

{{< alert "check" >}}
**Los tres funcionan en GitHub Pages gratis. Pero cada uno tiene su personalidad.**
{{< /alert >}}

---

## 📄 HTML plano — El clásico

{{< alert "check" >}}
**Así empezábamos — HTML a pelo, sin frameworks, sin build.**
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

## ⚡ Hugo — El que usamos ahora

{{< alert "pencil" >}}
**Go — Single binary. Escribes Markdown y Hugo genera el HTML. El que usamos para esta web.**
{{< /alert >}}

```go
<html>
  <head><title>{{ .Title }}</title></head>
  <body>{{ block "main" }}{{ .Content }}{{ end }}</body>
</html>
```

| ✅ Pros | ❌ Contras |
|---|---|
| Rapidísimo (<1ms/página) | Curva de aprendizaje |
| Markdown + temas con Tailwind | Sistema de templates propio |
| Multilenguaje integrado | |

{{< badge >}}
🚀 Build ultrarrápido
{{< /badge >}}
{{< badge >}}
🎨 Temas pre-hechos
{{< /badge >}}
{{< badge >}}
📝 Blog nativo
{{< /badge >}}
{{< badge >}}
🌍 Multilenguaje
{{< /badge >}}

---

## 💎 Jekyll — Nativo de GitHub Pages

{{< alert "info" >}}
**Ruby. Escribes Markdown con Liquid templates. Creado por el co-fundador de GitHub.**
{{< /alert >}}

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
| GitHub lo compila solo — sin build local | Lento en builds grandes |
| Sin instalar nada local | Ruby pesado de instalar |
| El más veterano (2010) | |

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

## 🏗️ Arquitectura

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
✏️ Escribes .md → 📦 git push → 💎 GitHub compila → 🌍 GitHub Pages
```

{{< alert "info" >}}
Con Jekyll, no necesitas instalar nada local. GitHub ejecuta Jekyll por ti automáticamente.
{{< /alert >}}

---

## 🤔 ¿Cuál usar?

| Situación | Recomendación |
|---|---|
| Landing de 1 página | ✅ HTML plano |
| Blog personal pequeño | 💎 Jekyll |
| Documentación técnica grande | ⚡ Hugo |
| Portfolio visual | ⚡ Hugo (Blowfish, PaperMod) |
| Sin ganas de instalar nada local | 💎 Jekyll |

💡 **Dato:** El sitio de Hermes Agent (hermes-agent.nousresearch.com) usa Hugo. También la documentación de **Google**, **Kubernetes** y **Docker**.