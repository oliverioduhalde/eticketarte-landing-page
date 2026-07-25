# 🚀 Configuración de Vercel - E-TicketArte Landing Page

## 📌 Arquitectura

```
GitHub (eticketarte-landing-page) 
        ↓ (push automático)
    Vercel (Deploy automático)
        ↓ (CNAME pointing)
  www.eticketarte.com (Dominio en Wix)
```

---

## 🎯 Pasos para Configurar Vercel

### **Paso 1: Crear Cuenta en Vercel**
1. Ve a [vercel.com](https://vercel.com)
2. Haz clic en "Sign Up"
3. Elige "Continue with GitHub"
4. Autoriza la conexión con tu cuenta GitHub (oliverioduhalde)

### **Paso 2: Importar Proyecto desde GitHub**
1. En Vercel Dashboard, haz clic en "New Project"
2. Busca "eticketarte-landing-page"
3. Selecciona el repositorio
4. Haz clic en "Import"

### **Paso 3: Configurar Proyecto**
```
Project Name: eticketarte-landing-page
Root Directory: ./
Build Command: (dejar en blanco)
Output Directory: (dejar en blanco)
```

### **Paso 4: Desplegar**
1. Haz clic en "Deploy"
2. Espera a que termine (2-3 minutos)
3. Vercel te dará una URL: eticketarte-landing-page.vercel.app

### **Paso 5: Conectar Dominio de Wix a Vercel**

#### En Wix:
1. Dashboard → Settings → Domains
2. Selecciona "eticketarte.com"
3. Selecciona "Connect to External Host" o "DNS Records"
4. Agrega estos DNS records:

```
Tipo: CNAME
Nombre: www
Valor: cname.vercel-dns.com.
TTL: 3600
```

#### En Vercel:
1. Dashboard → Tu Proyecto → Settings → Domains
2. Agrega "eticketarte.com" y "www.eticketarte.com"
3. Sigue las instrucciones de Vercel

---

## 🔄 Workflow de Actualización

**Con Vercel el deploy es automático:**

```bash
# En tu máquina local
git add .
git commit -m "Update landing page"
git push origin main

# Automático en Vercel (sin hacer nada!)
# → Vercel detecta el cambio
# → Construye y despliega
# → www.eticketarte.com actualizado en ~1 minuto
```

---

## 📊 URLs

| URL | Propósito |
|-----|-----------|
| `eticketarte-landing-page.vercel.app` | Preview |
| `www.eticketarte.com` | Sitio en vivo |

---

## ✅ Checklist

- [ ] Vercel account creado (conectado a GitHub)
- [ ] Proyecto importado en Vercel
- [ ] Deploy exitoso
- [ ] Dominio Wix apunta a Vercel
- [ ] www.eticketarte.com funciona
- [ ] Testing completado

---

**Última actualización:** 25 de Julio, 2026
