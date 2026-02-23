# REWEAR — Plataforma de Moda Sostenible
> Proyecto de Diseño de Interfaces Web

---

## 📁 Estructura del Proyecto

```
Proyecto/
├── index.html          # Página principal (home)
├── shop.html           # Tienda / catálogo de productos
├── auth.html           # Login y registro de usuarios
├── dashboard.html      # Dashboard de ventas y estadísticas
├── comparativa.html    # Comparativa de planes y servicios
├── sitemap.xml         # Mapa del sitio (SEO)
├── css/
│   ├── styles.css      # Estilos generales (index + shop)
│   ├── auth.css        # Estilos página de autenticación
│   └── shop.css        # Estilos adicionales de tienda
└── img/
    ├── favicon.svg     # Favicon vectorial personalizado
    └── favicon-32x32.png
```

---

## 🎯 Criterios de la Rúbrica — Implementación

### 1️⃣ Tablas HTML5
**Archivos:** `shop.html`, `dashboard.html`, `comparativa.html`

Se han implementado **7 tablas** con toda la semántica requerida:

- `<thead>`, `<tbody>`, `<tfoot>` en todas las tablas
- `colspan` y `rowspan` para estructuras complejas
- Atributo `scope="col"` y `scope="row"` para accesibilidad
- `<caption>` descriptivo en cada tabla
- Roles ARIA (`role="table"`, `aria-labelledby`)

```html
<!-- Ejemplo con colspan + rowspan + scope + caption -->
<table role="table" aria-labelledby="caption1">
    <caption id="caption1">Comparativa Completa de Planes</caption>
    <thead>
        <tr>
            <th scope="col" rowspan="2">Características</th>
            <th scope="colgroup" colspan="3">Planes disponibles</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">Envío gratuito</th>
            <td>✗</td>
            <td>✓</td>
            <td>✓</td>
        </tr>
    </tbody>
</table>
```

---

### 2️⃣ Background
**Archivo:** `css/styles.css`, `css/auth.css`

Se usan **múltiples capas** de background combinando imagen real, gradiente y patrón SVG:

```css
.hero {
    background-image:
        /* Capa 1: gradiente overlay */
        linear-gradient(135deg, rgba(249,250,251,0.92), rgba(243,244,246,0.88)),
        /* Capa 2: imagen real de Unsplash */
        url('https://images.unsplash.com/photo-1558769132-cb1aea941c88?w=1920'),
        /* Capa 3: patrón SVG inline */
        url('data:image/svg+xml,...');

    background-position: center, top right, top left;
    background-size: cover, cover, 60px 60px;
    background-attachment: scroll, fixed, fixed; /* parallax */
    background-origin: padding-box, border-box, padding-box;
    background-clip: padding-box, border-box, padding-box;
}
```

Propiedades usadas: `background-color`, `background-image`, `background-repeat`, `background-position`, `background-size`, `background-attachment`, `background-origin`, `background-clip`, `background-blend-mode`.

---

### 3️⃣ Flexbox
**Archivo:** `css/styles.css`

Flexbox se usa extensivamente y está documentado con comentarios:

```css
/* Filter Tabs - Flexbox con wrap para diseño responsive */
.filter-tabs {
    display: flex;
    flex-wrap: wrap;           /* permite que los items salten de línea */
    justify-content: center;   /* centrado horizontal */
    align-items: center;       /* centrado vertical */
    gap: 0.5rem;
}

/* Navegación - distribución horizontal */
.nav-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

Propiedades usadas: `display:flex`, `flex-direction`, `flex-wrap`, `justify-content`, `align-items`, `align-self`, `flex`, `flex-grow`, `gap`.

---

### 4️⃣ Formato de Texto
**Archivos:** `css/styles.css`, `css/auth.css`

```css
/* Tipografía Google Fonts */
font-family: 'Inter', sans-serif;

/* Transformaciones */
text-transform: uppercase;          /* etiquetas y badges */
text-decoration: line-through;      /* precios tachados */
letter-spacing: 0.05em;             /* encabezados y footer */
line-height: 1.7;                   /* párrafos de contenido */
text-indent: 0.5rem;                /* párrafos de descripción */
vertical-align: middle;             /* alineación de iconos SVG */

/* Tipografía fluida responsive */
font-size: clamp(2rem, 5vw, 4rem);
```

---

### 5️⃣ Formularios
**Archivo:** `auth.html`

Formulario completo con login y registro:

```html
<!-- Fieldset y Legend para agrupar campos -->
<fieldset class="form-fieldset">
    <legend>Información Personal</legend>

    <!-- Label correctamente asociado -->
    <label for="reg-email" class="form-label">Correo electrónico</label>
    <input type="email" id="reg-email" name="email"
        required autocomplete="email" pattern="[^@]+@[^@]+\.[^@]+">

    <!-- Array de checkboxes -->
    <input type="checkbox" name="categorias[]" value="mujer">
    <input type="checkbox" name="categorias[]" value="hombre">
</fieldset>
```

Tipos de input usados: `text`, `email`, `password`, `checkbox`, `radio`, `select`, `textarea`.
Validaciones: `required`, `minlength`, `maxlength`, `pattern`, `autocomplete`.
Extras: medidor de fuerza de contraseña (JS), contador de caracteres.

---

### 6️⃣ Favicon
**Archivos:** Todos los HTML

Favicon personalizado con logo Rewear (símbolo de reciclaje + percha):

```html
<link rel="icon" type="image/svg+xml" href="img/favicon.svg">
<link rel="icon" type="image/png" sizes="32x32" href="img/favicon-32x32.png">
<link rel="apple-touch-icon" sizes="180x180" href="img/favicon-32x32.png">
```

Implementado en las 5 páginas. Incluye SVG escalable, PNG y Apple Touch Icon.

---

### 7️⃣ Enlaces Internos (`#id`)
**Archivos:** Todos los HTML

Navegación interna con scroll suave en todas las páginas:

```html
<!-- Ancla de destino -->
<nav id="top" class="nav">...</nav>
<section id="inicio">...</section>
<section id="colecciones">...</section>

<!-- Botón volver arriba (position: fixed) -->
<a href="#top" id="back-to-top" class="back-to-top" aria-label="Volver arriba">↑</a>
```

```javascript
// JavaScript para mostrar el botón y scroll suave
window.addEventListener('scroll', () => {
    backToTop.classList.toggle('visible', window.scrollY > 300);
});
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', e => {
        target.scrollIntoView({ behavior: 'smooth' });
    });
});
```

Scroll suave también activado por CSS: `<html class="scroll-smooth">`.

---

### 8️⃣ Meta Tags
**Archivos:** Todos los HTML

Implementación completa en todas las páginas:

```html
<!-- SEO básico -->
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="robots" content="index, follow">
<meta name="description" content="Rewear - Moda sostenible premium...">
<meta name="keywords" content="rewear, moda sostenible, segunda mano">
<meta name="author" content="Rewear">
<meta name="theme-color" content="#1f2937">
<link rel="canonical" href="https://rewear.com/">

<!-- Open Graph (redes sociales) -->
<meta property="og:title" content="Rewear - Moda Sostenible Premium">
<meta property="og:description" content="...">
<meta property="og:image" content="https://...">
<meta property="og:type" content="website">
<meta property="og:url" content="https://rewear.com/">

<!-- JSON-LD Structured Data (SEO avanzado) -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Rewear",
  "url": "https://rewear.com"
}
</script>
```

Además se incluye `sitemap.xml` con las 5 páginas del proyecto.

---

## 🗺️ Navegación entre páginas

Todas las páginas están interconectadas mediante la barra de navegación:

| Página | Acceso desde |
|--------|-------------|
| `index.html` | Logo REWEAR en todas las páginas |
| `shop.html` | Nav link "Tienda" en todas las páginas |
| `auth.html` | Nav link "Mi Cuenta" / icono de perfil |
| `dashboard.html` | Nav link "Dashboard" en todas las páginas |
| `comparativa.html` | Nav link "Comparativa" en todas las páginas |

---

## 🛠️ Tecnologías Usadas

- **HTML5** semántico (`<header>`, `<main>`, `<nav>`, `<section>`, `<article>`, `<aside>`, `<footer>`)
- **CSS3** con variables (`--custom-properties`), Flexbox, animaciones
- **Tailwind CSS** (CDN) para utilidades adicionales
- **Google Fonts** — Inter (300, 400, 500, 600, 700, 800)
- **JavaScript** vanilla para interacciones UI
- **Schema.org** JSON-LD para datos estructurados

---

## ✅ Checklist de Criterios

- [x] Tablas HTML5 con thead/tbody/tfoot/colspan/rowspan/scope/caption
- [x] Background con múltiples capas, imagen, clip, origin, attachment
- [x] Flexbox con wrap, direction, justify, align documentados
- [x] Formato de texto: transform, decoration, letter-spacing, line-height, indent
- [x] Formularios con fieldset, legend, label, name[], validación HTML5
- [x] Favicon SVG + PNG en todas las páginas
- [x] Enlaces internos con #id y botón back-to-top en todas las páginas
- [x] Meta tags: charset, viewport, robots, description, OG, JSON-LD, canonical
