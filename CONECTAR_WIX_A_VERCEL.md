# 🔗 Guía: Conectar Dominio Wix con Vercel

## 📌 Objetivo
Hacer que www.eticketarte.com apunte a tu landing page en Vercel.

---

## 🚀 PROCESO RECOMENDADO (Opción A + Vercel)

### FASE 1: Crear y Desplegar en Vercel (PRIMERO)

**Paso 1: Crear cuenta en Vercel**

1. Ve a [vercel.com](https://vercel.com)
2. Haz clic en **Sign Up**
3. Selecciona: **Continue with GitHub**
4. Autoriza el acceso a tu cuenta GitHub (oliverioduhalde)

**Paso 2: Importar proyecto**

1. En Vercel Dashboard, haz clic en **New Project**
2. Busca: **eticketarte-landing-page**
3. Haz clic en el repositorio
4. Haz clic en **Import**

**Paso 3: Configurar (deja por defecto)**

```
Project Name: eticketarte-landing-page
Root Directory: ./
Build Command: (dejar en blanco)
Output Directory: (dejar en blanco)
```

5. Haz clic en **Deploy**
6. Espera ~2-3 minutos

**Resultado esperado:**
```
✅ Deployment Success!
Your project is live at: 
https://eticketarte-landing-page.vercel.app
```

**GUARDA ESTA URL.**

---

### FASE 2: Agregar Dominio en Vercel

**En Vercel Dashboard:**

1. Abre tu proyecto: **eticketarte-landing-page**
2. Haz clic en **Settings** (arriba a la derecha)
3. En el menú izquierdo: **Domains**
4. Haz clic en **Add Domain**
5. Escribe: **eticketarte.com** (sin www)
6. Haz clic en **Add Domain**

**Vercel te mostrará los registros DNS:**

```
Para agregar eticketarte.com necesitas:

Option 1: Change Nameservers to:
- ns1.vercel-dns.com
- ns2.vercel-dns.com
- ns3.vercel-dns.com
- ns4.vercel-dns.com

Option 2: Add CNAME Record:
- Name: www
- Type: CNAME
- Value: cname.vercel-dns.com
```

**COPIA ESTOS DATOS.**

---

### FASE 3: Configurar en Wix

**En tu navegador, abre:**
```
https://www.wix.com/dashboard
```

**Haz login con:**
```
Email: oliverio.duhalde@gmail.com
Contraseña: [Tu contraseña Wix]
```

**Paso 1: Acceder a Dominios**

1. Haz clic en tu sitio **eticketarte.com** en el dashboard
2. Haz clic en **Settings** (abajo a la izquierda)
3. Busca **Domains** o **Mis Dominios**
4. Haz clic en **eticketarte.com**

**Paso 2: Cambiar Nameservers (OPCIÓN A - Más fácil)**

1. Busca: **"Change Nameservers"** o **"Edit Nameservers"**
2. Selecciona: **"I want to use external nameservers"** o similar
3. En los campos de nameservers, ingresa:

```
Nameserver 1: ns1.vercel-dns.com
Nameserver 2: ns2.vercel-dns.com
Nameserver 3: ns3.vercel-dns.com
Nameserver 4: ns4.vercel-dns.com
```

4. Haz clic: **Save** o **Guardar**
5. Verás un mensaje: "Nameservers updated successfully"

---

**OPCIÓN B (Si prefieres no cambiar nameservers):**

1. Ve a: **Settings → Domains → eticketarte.com**
2. Busca: **DNS Records**, **Advanced**, o **DNS Settings**
3. Haz clic en **Add Record** o **+ New Record**

**Agrega estos registros:**

```
Registro 1:
Name: @  (o dejar en blanco)
Type: CNAME
Value: cname.vercel-dns.com
TTL: 3600

Registro 2:
Name: www
Type: CNAME
Value: cname.vercel-dns.com
TTL: 3600
```

4. Haz clic en **Save** para cada registro

---

### FASE 4: Esperar Propagación DNS

```
Tiempo estimado: 15 minutos a 48 horas
(Generalmente: 2-4 horas)
```

**Mientras esperas:**
- Verifica que el deploy en Vercel está en "Ready"
- Revisa que los nameservers en Wix se guardaron

---

### FASE 5: Verificar que Funciona

**Opción 1: Visitar el sitio**

1. Abre tu navegador
2. Ve a: **https://www.eticketarte.com**
3. Deberías ver tu landing page de E-TicketArte

**Opción 2: Verificar DNS (en Terminal)**

```bash
# En tu Mac, abre Terminal y ejecuta:
nslookup eticketarte.com

# Deberías ver algo como:
# eticketarte.com
# Name: cname.vercel-dns.com
# Address: [IP Address]
```

**Opción 3: Verificar en Vercel**

1. Vercel Dashboard → Tu Proyecto → Settings → Domains
2. Deberías ver:
```
✅ eticketarte.com (Verified)
✅ www.eticketarte.com (Verified)
```

---

## 🚨 Si No Funciona

### "Aún me redirige a Wix"
- Espera más tiempo (DNS propaga lentamente)
- Limpia cache: Cmd+Shift+R en Mac
- Prueba en navegador privado/incógnito
- Verifica nameservers en Wix están correctos

### "Veo error 404 o "Site Not Found""
- En Vercel: Verifica que el deploy esté en "Ready"
- En Vercel: Verifica que eticketarte.com esté agregado en Domains
- Revisa en: https://eticketarte-landing-page.vercel.app (preview)
- Si preview funciona pero dominio no, es problema de DNS

### "DNS checker dice que no está propagado"
- Es normal, espera más horas
- Usa: https://dnschecker.org para monitorear
- Verifica nameservers en: https://www.whatsmydns.net

---

## ✅ Checklist Final

- [ ] Vercel account creado (con GitHub conectado)
- [ ] Proyecto importado en Vercel
- [ ] Deploy exitoso (estado: "Ready")
- [ ] Preview funciona: eticketarte-landing-page.vercel.app
- [ ] Dominio agregado en Vercel
- [ ] Registros DNS obtenidos de Vercel
- [ ] Nameservers cambiados EN WIX (o DNS agregados)
- [ ] Esperé 15+ minutos para propagación
- [ ] www.eticketarte.com funciona ✅
- [ ] HTTPS funciona (candado verde)

---

## 🎯 Próximo Paso

Una vez funcione www.eticketarte.com:

**Flujo automático:**
```
1. Editas index.html en GitHub
2. Haces: git add . && git commit -m "..." && git push
3. Vercel detecta el cambio automáticamente
4. Despliega en 1-2 minutos
5. Cambios viven en www.eticketarte.com ✨
```

---

**Ahora comienza: Ve a vercel.com y crea tu cuenta**

Última actualización: 25 de Julio, 2026
