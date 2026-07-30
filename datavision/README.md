# DataVision Academy - Sitio Web Editable

## 🚀 ¿Cómo usar este proyecto en Visual Code?

### 1. **Descargar el archivo**
- Descarga `index.html` desde aquí
- Guárdalo en una carpeta (ej: `mi-academia/`)

### 2. **Abrir en Visual Code**
```bash
# Abre Visual Code
# Usa Ctrl+K Ctrl+O (Windows/Linux) o Cmd+K Cmd+O (Mac)
# Selecciona la carpeta donde está index.html
```

### 3. **Ver en vivo**
- Instala la extensión **"Live Server"** de Ritwick Dey
- Haz clic derecho en `index.html` → "Open with Live Server"
- El sitio se abrirá en tu navegador y se actualizará automáticamente al guardar cambios

---

## 🎨 Elementos principales para personalizar

### **Cambiar colores**
En la sección `:root` (líneas 22-28):
```css
--primary: #6366f1;        /* Color azul → cambiar aquí */
--secondary: #ec4899;      /* Color rosa → cambiar aquí */
--bg-dark: #0f172a;        /* Fondo oscuro */
--text-dark: #1e293b;      /* Texto oscuro */
```

**Ejemplo:** Para usar azul oscuro:
```css
--primary: #1e3a8a;        /* Azul oscuro */
--secondary: #0891b2;      /* Azul cian */
```

### **Cambiar nombre de la academia**
Línea 88 (Navbar):
```html
<a href="#" class="logo">📊 DataVision</a>
<!-- Cambiar "DataVision" por tu nombre -->
```

Línea 310 (Footer):
```html
<p>&copy; 2024 DataVision Academy. Transformando carreras...</p>
```

### **Cambiar programas ofertados**
Las tarjetas de programas están en las líneas 193-246. Cada programa tiene:
```html
<div class="program-card">
    <h3>🤖 AI Engineer</h3>           <!-- Nombre del programa -->
    <p class="price">$699</p>          <!-- Precio -->
    <p>14 semanas | Bootcamp...</p>    <!-- Duración -->
    <ul>
        <li>LLMs y Transformers</li>   <!-- Cambiar beneficios -->
        ...
    </ul>
</div>
```

### **Cambiar números de estadísticas**
Líneas 165-175 (Stats):
```html
<h3>+5,000</h3>                   <!-- Cambiar número -->
<p>Estudiantes Activos</p>         <!-- Cambiar texto -->
```

### **Cambiar testimonios**
Líneas 269-305:
```html
<div class="testimonial-card">
    <div class="stars">★★★★★</div>
    <p>"Aquí va el testimonio..."</p>
    <div class="testimonial-author">- Nombre | Ciudad</div>
</div>
```

### **Cambiar información de contacto**
Línea 330 (Footer):
```html
Contacto: <a href="tel:+51999999999">+51 999 999 999</a> | 
<a href="mailto:hola@datavision.com">hola@datavision.com</a>
```

---

## 📊 Gestión de Leads (Inscripciones)

El formulario guarda automáticamente los datos en **localStorage** (almacenamiento local del navegador).

### **Ver leads capturados:**
1. Abre el sitio en navegador
2. Presiona `F12` (Abrir DevTools)
3. Ve a la pestaña "Console"
4. Escribe: `verLeads()`
5. Verás una tabla con todos los contactos

### **Exportar leads:**
En la consola (F12):
```javascript
// Copiar los datos
JSON.stringify(verLeads(), null, 2)

// O guardar como JSON
const data = JSON.stringify(verLeads());
console.save(data, 'leads.json');
```

### **Conectar a backend real:**
En la función `handleSubmit()` (línea 378), reemplaza:
```javascript
// ACTUAL (guarda en navegador):
let leads = JSON.parse(localStorage.getItem('leads')) || [];
leads.push(formData);
localStorage.setItem('leads', JSON.stringify(leads));

// POR ESTO (envía a servidor):
fetch('https://tu-backend.com/api/leads', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(formData)
})
.then(res => res.json())
.then(data => console.log('Guardado:', data));
```

---

## 🎯 Optimizaciones para capturar más leads

### 1. **Agregar más CTAs (Call-to-Action)**
```html
<!-- Botón flotante en esquina inferior derecha -->
<div style="position: fixed; bottom: 20px; right: 20px; z-index: 999;">
    <a href="https://wa.me/51999999999" 
       style="display: inline-block; background: #25D366; color: white; 
              padding: 15px 20px; border-radius: 50px; 
              text-decoration: none; font-weight: bold;">
        💬 Chatea con nosotros
    </a>
</div>
```

### 2. **Agregar popup de newsletter**
```html
<!-- Agrega antes de </body> -->
<div id="newsletterPopup" style="display: none; position: fixed; 
     top: 50%; left: 50%; transform: translate(-50%, -50%); 
     background: white; padding: 2rem; border-radius: 1rem; 
     z-index: 1000; box-shadow: 0 10px 40px rgba(0,0,0,0.3);">
    <h3>Recibe actualizaciones gratis</h3>
    <input type="email" placeholder="tu@email.com" style="width: 100%; padding: 0.8rem; margin: 1rem 0; border: 1px solid #ccc; border-radius: 0.5rem;">
    <button style="width: 100%; padding: 0.8rem; background: #6366f1; color: white; border: none; border-radius: 0.5rem; cursor: pointer;">Suscribirse</button>
</div>
```

### 3. **Agregar contador de visitantes**
```html
<!-- Agregar en footer -->
<p style="font-size: 0.8rem; opacity: 0.6;">
    Visitantes hoy: <span id="visitors">0</span>
</p>

<script>
    // Contar visitantes
    let visitors = parseInt(localStorage.getItem('visitors')) || 0;
    visitors++;
    localStorage.setItem('visitors', visitors);
    document.getElementById('visitors').textContent = visitors;
</script>
```

---

## 📱 Responsive Design

El sitio ya es **100% mobile-friendly**. Puedes verlo:
1. Presiona `F12` en navegador
2. Haz clic en el icono de dispositivo móvil
3. Selecciona iPhone o Android

---

## ⚡ Performance & SEO

### Meta tags importantes (edita líneas 5-7):
```html
<meta name="description" content="Academia de Data...">
<title>DataVision Academy - Escuela de Data e IA</title>
```

### Para Google Analytics, agrega antes de `</head>`:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_XXXXXXX');
</script>
```

---

## 🔗 Hosting Gratis

### **Opción 1: GitHub Pages (MEJOR)**
1. Crea cuenta en github.com
2. Crea repositorio: `mi-academia`
3. Sube `index.html`
4. Ve a Settings → Pages → Source: main branch
5. Tu sitio estará en: `https://tuusuario.github.io/mi-academia`

### **Opción 2: Vercel (Para Next.js)**
1. Crea cuenta en vercel.com
2. Conecta tu GitHub
3. Despliega en 1 click

### **Opción 3: Netlify**
1. Arrastra `index.html` a netlify.com
2. Tu sitio está live

---

## 📋 Checklist antes de lanzar

- [ ] Cambiar nombre de academia
- [ ] Cambiar colores a tu marca
- [ ] Actualizar programas ofertados
- [ ] Cambiar precios reales
- [ ] Agregar testimonios reales
- [ ] Configurar formulario (backend)
- [ ] Agregar email/WhatsApp real
- [ ] Configurar Google Analytics
- [ ] Prueba en móvil (F12 + responsive)
- [ ] Prueba formulario
- [ ] Subir a dominio propio

---

## 🆘 Problemas comunes

**El sitio no se ve bien en móvil:**
- Asegúrate que el viewport meta tag esté correcto
- Prueba con F12 → Responsive Design

**Los estilos no se actualizan:**
- Presiona Ctrl+Shift+R (limpiar caché)

**El formulario no guarda datos:**
- Abre F12 → Console
- Escribe: `localStorage`
- Verifica que no esté deshabilitado en privacidad

---

## 💡 Próximos pasos

1. **Agregar base de datos real**: Firebase, Supabase o MongoDB
2. **Agregar email automático**: Formspree, EmailJS
3. **Agregar pago**: Stripe, PayPal
4. **Agregar chat en vivo**: Tawk.to, Intercom
5. **Agregar blog**: Integrar CMS como Sanity o Contentful

---

**¿Preguntas?** Edita el HTML y experimenta. ¡Los cambios se verán en tiempo real con Live Server!

