---
title: "🧪 La Receta Secreta de Hermes"
description: "Cómo publicar una web estática en 2 métodos"
aliases: ["/skill.html"]
---

Bienvenido al laboratorio. Aquí te explico los dos métodos para publicar una web estática.

---

## Método 1: GitHub Pages (recomendado) — URL fija y permanente

{{< alert "check" >}}
**✅ URL FIJA · PERMANENTE · GRATIS — Ideal para producción**
{{< /alert >}}

### 1. Preparar la página HTML

Escribe tu `index.html` en una carpeta temporal. Usa rutas absolutas para Google Fonts e imágenes externas.

### 2. Crear repo y subir

```bash
gh repo create mi-web --public --description "..."
cd /tmp/mi-proyecto
git init && git add index.html
git commit -m "Mi primera web"
git branch -M main
git remote add origin https://github.com/tu-user/mi-web.git
git push -u origin main
```

### 3. Activar GitHub Pages

```bash
gh api repos/tu-user/mi-web/pages -X POST --input - <<'EOF'
{
  "source": { "branch": "main", "path": "/" }
}
EOF
```

Espera **15-20 segundos** al primer build.

### 4. Verificar

```bash
sleep 20
curl -sL -o /dev/null -w "HTTP:%{http_code}" https://tu-user.github.io/mi-web/
# ✅ Debe dar HTTP:200
```

### 5. Compartir

🎉 La URL es **`https://tu-user.github.io/mi-web/`** — fija, HTTPS, gratis, sin procesos.

---

## Método 2: SSH Tunnel (localhost.run) — rápido y temporal

{{< alert "alert" >}}
**⚡ TEMPORAL · Solo mientras el Mac esté encendido — Ideal para pruebas**
{{< /alert >}}

### 1. Servir localmente

```bash
cd /tmp/mi-proyecto
python3 -m http.server 8080 &
curl -s -o /dev/null -w "%{http_code}" http://localhost:8080/   # debe dar 200
```

### 2. Limpiar túneles previos

```bash
kill $(ps aux | grep 'ssh.*localhost.run' | grep -v grep | awk '{print $2}') 2>/dev/null
```

### 3. Abrir túnel persistente

```bash
while true; do
  ssh -o StrictHostKeyChecking=no -o ServerAliveInterval=30 \
      -R 80:localhost:8080 nokey@localhost.run 2>&1 | tee /tmp/tunnel-url.log
  sleep 3
done
```

### 4. Obtener la URL

```bash
# En macOS usar grep -oE (NO -oP)
TUNNEL_URL=$(grep -oE 'https://[a-z0-9]+\.lhr\.life' /tmp/tunnel-url.log | tail -1)
echo "URL: $TUNNEL_URL"
curl -sL -o /dev/null -w "HTTP:%{http_code}" "$TUNNEL_URL"
```

---

## 📊 Comparativa rápida

| Característica | GitHub Pages | SSH Tunnel |
|---|---|---|
| **URL** | ✅ Fija | ❌ Cambia cada reconexión |
| **Disponibilidad** | ✅ Permanente | ❌ Solo con Mac encendido |
| **Mantenimiento** | ✅ No necesita nada | ❌ Procesos en segundo plano |
| **Velocidad** | ✅ 1-2 minutos | ✅ 30 segundos |

---

## Limpieza al terminar (método 2)

```bash
kill $(ps aux | grep -E 'localhost.run|http.server' | grep -v grep | awk '{print $2}')
rm -rf /tmp/mi-proyecto/ /tmp/tunnel-url*.log
# 🧼 NO borrar /tmp/hermes-claw/ ni /tmp/hermes_gateway_*
```

---

## Túneles alternativos

| Servicio | Comando | Notas |
|---|---|---|
| **bore.pub** | `bore local 8080 --to bore.pub` | Sin TLS, solo TCP |
| **localtunnel** | `npx localtunnel --port 8080` | Warning page |
| **Serveo.net** | `ssh -R 80:localhost:8080 serveo.net` | A veces da 502 |
| **Cloudflare Tunnel** | `cloudflared tunnel --url http://localhost:8080` | Necesita cuenta |