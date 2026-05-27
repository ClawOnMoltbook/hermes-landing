---
title: "🌐 Web estática vs dinámica"
description: "Diferencias entre webs estáticas (como esta) y dinámicas (redes sociales, tiendas)"
aliases: ["/web-estatica-vs-dinamica.html"]
---

{{< typeit >}}Tu web no necesita un servidor... descubre por qué {{< /typeit >}}

{{< alert "check" >}}
**¿Por qué tu landing de Hermes puede vivir en GitHub Pages gratis y Facebook no? Aquí te lo explico.**
{{< /alert >}}

---

## 📄 Web estática — Cómo funciona esta página

```
🌍 Navegador → ⚡ CDN → 📦 GitHub Pages
```

Tu navegador pide la URL → GitHub te envía el HTML tal cual → lo pintas. **Fin.**

**Tiempo total:** ~0.3 segundos

{{< alert "check" >}}
**No hay servidores, no hay bases de datos, no hay lógica. Solo un archivo HTML que GitHub te sirve.**
{{< /alert >}}

---

## ⚡ Web dinámica — Cómo funciona una red social

```
🌍 Navegador → 🖥️ Servidor → 🗄️ Base de datos
                       ↕
                  ¿quién eres?
                  ¿qué posts hay nuevos?
                  ¿qué te gusta?
```

**Tiempo total:** ~0.5-3 segundos (y consume CPU)

Cada visita es **única**. El servidor construye la página en el momento con tus datos.

---

## 📊 Comparativa

| | 📄 Estática | ⚡ Dinámica |
|---|---|---|
| **Analogía** | 📖 Un libro | 📋 Una pizarra |
| **Contenido** | Todos ven lo mismo | Cada quien ve algo distinto |
| **Servidor** | No necesita | Necesita servidor + BD |
| **Lenguajes** | HTML/CSS/JS | PHP, Node, Python, Ruby |
| **Ejemplos** | Esta landing, documentación | Facebook, Twitter, TikTok |
| **Coste hosting** | Gratis (GitHub Pages) | Desde 5€/mes |

---

## ✅ Qué puedes hacer en estática

{{< badge >}}
📄 Landing pages
{{< /badge >}}
{{< badge >}}
📚 Documentación
{{< /badge >}}
{{< badge >}}
🎨 Portfolios / CVs
{{< /badge >}}
{{< badge >}}
📝 Blogs (Hugo, Jekyll)
{{< /badge >}}
{{< badge >}}
🛍️ Páginas de producto
{{< /badge >}}
{{< badge >}}
🖼️ Galerías
{{< /badge >}}

## ❌ Qué NO puedes hacer sin backend

{{< badge >}}
🚫 Login/registro
{{< /badge >}}
{{< badge >}}
🚫 Foros/comentarios
{{< /badge >}}
{{< badge >}}
🚫 Chats
{{< /badge >}}
{{< badge >}}
🚫 Tiendas con carrito
{{< /badge >}}
{{< badge >}}
🚫 APIs dinámicas
{{< /badge >}}

---

## 🎯 Analogía: Libro vs Pizarra

**Estática = Un libro 📖** — Lo escribes una vez, todos leen lo mismo. No puedes cambiarlo sin reescribir.

**Dinámica = Una pizarra 📋** — Cada persona que llega puede escribir y ver algo distinto. Necesitas a alguien (el servidor) gestionando quién escribe qué.

---

## En resumen

Tu landing de Hermes es un **cartel en una pared**. Lo pones y todo el mundo ve lo mismo. No necesita un servidor porque el mensaje no cambia de una visita a otra.

Una red social o una tienda es un **mercado en movimiento**: cada persona ve cosas distintas, comenta, compra. Ahí sí necesitas servidores, bases de datos y lenguajes como PHP, Node o Python.

**Tu landing no necesita nada de eso. GitHub Pages es perfecto.**