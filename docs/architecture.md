# Leo's Coffee - System Architecture Document

## 1. Project Overview

**Project Name**: Leo's Coffee Website
**Location**: Greifswalder Str. 2, 10405 Berlin
**Project Root**: `/Users/m./berlinwebsites/168_Leo's Coffee`
**Technology Stack**: HTML5, CSS3, Vanilla JavaScript (ES6+)
**Target Audience**: Coffee enthusiasts, remote workers, breakfast seekers, tea lovers

### Key Features
- Extensive tea selection showcase
- Premium coffee offerings
- Breakfast menu presentation
- Laptop-friendly workspace promotion
- Photo gallery integration (11 Google Photos URLs)
- Location and contact information
- Customer reviews section

---

## 2. Folder Structure

```
/Users/m./berlinwebsites/168_Leo's Coffee/
├── index.html                          # Main entry point
├── docs/                               # Documentation
│   ├── architecture.md                 # This file
│   └── deployment.md                   # Deployment guide
├── src/                                # Source files
│   ├── css/                           # Stylesheets
│   │   ├── main.css                   # Main stylesheet (imports all)
│   │   ├── base/                      # Foundation styles
│   │   │   ├── reset.css              # CSS reset/normalize
│   │   │   ├── variables.css          # CSS custom properties
│   │   │   └── typography.css         # Font definitions
│   │   ├── layout/                    # Layout components
│   │   │   ├── header.css             # Header/navigation
│   │   │   ├── footer.css             # Footer
│   │   │   └── grid.css               # Grid system
│   │   ├── components/                # Reusable components
│   │   │   ├── buttons.css            # Button styles
│   │   │   ├── cards.css              # Card components
│   │   │   ├── forms.css              # Form elements
│   │   │   └── gallery.css            # Gallery component
│   │   ├── sections/                  # Page sections
│   │   │   ├── hero.css               # Hero section
│   │   │   ├── about.css              # About section
│   │   │   ├── menu.css               # Menu section
│   │   │   ├── location.css           # Location section
│   │   │   └── reviews.css            # Reviews section
│   │   └── utilities/                 # Utility classes
│   │       ├── spacing.css            # Margin/padding utilities
│   │       └── animations.css         # Animation definitions
│   ├── js/                            # JavaScript modules
│   │   ├── main.js                    # Main entry point
│   │   ├── modules/                   # ES6 modules
│   │   │   ├── gallery.js             # Gallery functionality
│   │   │   ├── smoothScroll.js        # Smooth scrolling
│   │   │   ├── formValidation.js      # Contact form validation
│   │   │   ├── lazyLoad.js            # Image lazy loading
│   │   │   ├── animations.js          # Scroll animations
│   │   │   └── navigation.js          # Mobile navigation
│   │   └── utils/                     # Utility functions
│   │       ├── debounce.js            # Debounce helper
│   │       └── observers.js           # Intersection Observer helpers
│   └── assets/                        # Static assets
│       ├── images/                    # Image files
│       │   ├── optimized/             # Optimized images
│       │   ├── placeholders/          # Low-quality placeholders
│       │   └── icons/                 # SVG icons
│       └── fonts/                     # Web fonts (if self-hosted)
├── config/                            # Configuration files
│   └── image-optimization.config.js   # Image optimization settings
└── scripts/                           # Build/utility scripts
    └── optimize-images.js             # Image optimization script
```

---

## 3. HTML Structure & Semantic Architecture

### 3.1 Page Structure

```html
<!DOCTYPE html>
<html lang="de">
<head>
  <!-- Meta Tags (SEO, Social, Viewport) -->
  <!-- Preload Critical Assets -->
  <!-- Stylesheets -->
</head>
<body>
  <!-- Skip to Content Link (Accessibility) -->
  <header role="banner">
    <!-- Navigation -->
  </header>

  <main role="main">
    <section id="hero" aria-label="Welcome">
      <!-- Hero Section -->
    </section>

    <section id="about" aria-labelledby="about-heading">
      <!-- About Section -->
    </section>

    <section id="menu" aria-labelledby="menu-heading">
      <!-- Menu Section (Coffee, Tea, Breakfast) -->
    </section>

    <section id="gallery" aria-labelledby="gallery-heading">
      <!-- Photo Gallery -->
    </section>

    <section id="features" aria-labelledby="features-heading">
      <!-- Features (Laptop-friendly, etc.) -->
    </section>

    <section id="reviews" aria-labelledby="reviews-heading">
      <!-- Customer Reviews -->
    </section>

    <section id="location" aria-labelledby="location-heading">
      <!-- Location & Map -->
    </section>

    <section id="contact" aria-labelledby="contact-heading">
      <!-- Contact Form -->
    </section>
  </main>

  <footer role="contentinfo">
    <!-- Footer Content -->
  </footer>

  <!-- Scripts (deferred) -->
  <!-- Schema.org Structured Data -->
</body>
</html>
```

### 3.2 Semantic HTML Patterns

**Navigation**
```html
<nav aria-label="Main navigation">
  <ul role="list">
    <li><a href="#about">Über Uns</a></li>
    <li><a href="#menu">Speisekarte</a></li>
    <li><a href="#gallery">Galerie</a></li>
    <li><a href="#location">Standort</a></li>
    <li><a href="#contact">Kontakt</a></li>
  </ul>
</nav>
```

**Menu Cards**
```html
<article class="menu-item" itemscope itemtype="https://schema.org/MenuItem">
  <img src="..." alt="..." loading="lazy" />
  <h3 itemprop="name">Cappuccino</h3>
  <p itemprop="description">...</p>
  <data itemprop="offers" itemscope itemtype="https://schema.org/Offer">
    <span itemprop="price">3.50</span>
    <meta itemprop="priceCurrency" content="EUR" />
  </data>
</article>
```

**Gallery**
```html
<div class="gallery" role="region" aria-label="Photo gallery">
  <figure>
    <img src="placeholder.jpg"
         data-src="optimized-image.jpg"
         alt="Interior of Leo's Coffee"
         loading="lazy" />
    <figcaption>Our cozy interior space</figcaption>
  </figure>
</div>
```

---

## 4. CSS Architecture

### 4.1 Design System

**Color Palette**
```css
:root {
  /* Primary Colors - Coffee Inspired */
  --color-primary-dark: #3E2723;      /* Dark espresso */
  --color-primary: #5D4037;            /* Coffee brown */
  --color-primary-light: #795548;      /* Milk coffee */

  /* Secondary Colors - Warm Accents */
  --color-secondary: #D7CCC8;          /* Cream */
  --color-secondary-light: #EFEBE9;    /* Light cream */
  --color-accent: #FF6F00;             /* Warm orange */

  /* Neutrals */
  --color-white: #FFFFFF;
  --color-gray-100: #F5F5F5;
  --color-gray-200: #EEEEEE;
  --color-gray-300: #E0E0E0;
  --color-gray-700: #616161;
  --color-gray-900: #212121;
  --color-black: #000000;

  /* Semantic Colors */
  --color-success: #4CAF50;
  --color-error: #F44336;
  --color-warning: #FF9800;
  --color-info: #2196F3;

  /* Typography */
  --font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --font-display: 'Playfair Display', Georgia, serif;
  --font-mono: 'Fira Code', 'Courier New', monospace;

  /* Font Sizes (Fluid Typography) */
  --font-size-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
  --font-size-sm: clamp(0.875rem, 0.8rem + 0.35vw, 1rem);
  --font-size-base: clamp(1rem, 0.9rem + 0.5vw, 1.125rem);
  --font-size-lg: clamp(1.125rem, 1rem + 0.625vw, 1.5rem);
  --font-size-xl: clamp(1.5rem, 1.3rem + 1vw, 2rem);
  --font-size-2xl: clamp(2rem, 1.6rem + 2vw, 3rem);
  --font-size-3xl: clamp(2.5rem, 2rem + 2.5vw, 4rem);

  /* Font Weights */
  --font-weight-light: 300;
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;

  /* Line Heights */
  --line-height-tight: 1.2;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.75;

  /* Spacing Scale (8px base) */
  --space-1: 0.25rem;   /* 4px */
  --space-2: 0.5rem;    /* 8px */
  --space-3: 0.75rem;   /* 12px */
  --space-4: 1rem;      /* 16px */
  --space-5: 1.5rem;    /* 24px */
  --space-6: 2rem;      /* 32px */
  --space-8: 3rem;      /* 48px */
  --space-10: 4rem;     /* 64px */
  --space-12: 6rem;     /* 96px */
  --space-16: 8rem;     /* 128px */

  /* Container Widths */
  --container-xs: 480px;
  --container-sm: 640px;
  --container-md: 768px;
  --container-lg: 1024px;
  --container-xl: 1280px;
  --container-2xl: 1536px;

  /* Border Radius */
  --radius-sm: 0.25rem;
  --radius-md: 0.5rem;
  --radius-lg: 1rem;
  --radius-xl: 1.5rem;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  --shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1);

  /* Transitions */
  --transition-fast: 150ms ease-in-out;
  --transition-base: 250ms ease-in-out;
  --transition-slow: 350ms ease-in-out;

  /* Z-Index Scale */
  --z-dropdown: 1000;
  --z-sticky: 1020;
  --z-fixed: 1030;
  --z-modal-backdrop: 1040;
  --z-modal: 1050;
  --z-popover: 1060;
  --z-tooltip: 1070;
}
```

### 4.2 Layout System

**Grid System**
```css
/* Container */
.container {
  width: 100%;
  max-width: var(--container-xl);
  margin-inline: auto;
  padding-inline: var(--space-4);
}

/* Grid Layouts */
.grid {
  display: grid;
  gap: var(--space-6);
}

.grid-2 { grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); }
.grid-3 { grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); }
.grid-4 { grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); }

/* Flexbox Utilities */
.flex { display: flex; }
.flex-col { flex-direction: column; }
.flex-wrap { flex-wrap: wrap; }
.items-center { align-items: center; }
.justify-between { justify-content: space-between; }
.gap-4 { gap: var(--space-4); }
```

### 4.3 Component Architecture

**Button Component**
```css
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: var(--space-3) var(--space-6);
  font-family: var(--font-primary);
  font-weight: var(--font-weight-medium);
  border-radius: var(--radius-md);
  transition: all var(--transition-base);
  cursor: pointer;
  border: none;
}

.btn-primary {
  background: var(--color-primary);
  color: var(--color-white);
}

.btn-primary:hover {
  background: var(--color-primary-dark);
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}
```

### 4.4 Responsive Breakpoints

```css
/* Mobile First Approach */
@media (min-width: 640px) { /* sm */ }
@media (min-width: 768px) { /* md */ }
@media (min-width: 1024px) { /* lg */ }
@media (min-width: 1280px) { /* xl */ }
@media (min-width: 1536px) { /* 2xl */ }
```

---

## 5. JavaScript Architecture

### 5.1 Module Pattern (ES6+)

**Main Entry Point** (`src/js/main.js`)
```javascript
import { initGallery } from './modules/gallery.js';
import { initSmoothScroll } from './modules/smoothScroll.js';
import { initFormValidation } from './modules/formValidation.js';
import { initLazyLoad } from './modules/lazyLoad.js';
import { initAnimations } from './modules/animations.js';
import { initNavigation } from './modules/navigation.js';

// DOM Ready
document.addEventListener('DOMContentLoaded', () => {
  initNavigation();
  initSmoothScroll();
  initGallery();
  initLazyLoad();
  initAnimations();
  initFormValidation();
});
```

### 5.2 Gallery Module

**Features**:
- Lightbox functionality
- Keyboard navigation
- Touch/swipe support
- Lazy loading integration
- Progressive image loading (LQIP - Low Quality Image Placeholder)

**Architecture**:
```javascript
// src/js/modules/gallery.js
export class Gallery {
  constructor(selector, options = {}) {
    this.gallery = document.querySelector(selector);
    this.options = {
      lazyLoad: true,
      lightbox: true,
      transition: 'fade',
      ...options
    };
    this.currentIndex = 0;
    this.images = [];
    this.init();
  }

  init() {
    this.loadImages();
    this.bindEvents();
    if (this.options.lightbox) this.initLightbox();
  }

  loadImages() { /* ... */ }
  bindEvents() { /* ... */ }
  openLightbox(index) { /* ... */ }
  closeLightbox() { /* ... */ }
  nextImage() { /* ... */ }
  prevImage() { /* ... */ }
}
```

### 5.3 Lazy Loading Strategy

```javascript
// src/js/modules/lazyLoad.js
export function initLazyLoad() {
  const imageObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const img = entry.target;
        loadImage(img);
        observer.unobserve(img);
      }
    });
  }, {
    rootMargin: '50px 0px',
    threshold: 0.01
  });

  document.querySelectorAll('img[data-src]').forEach(img => {
    imageObserver.observe(img);
  });
}

function loadImage(img) {
  const src = img.dataset.src;
  if (!src) return;

  img.src = src;
  img.classList.add('loaded');
}
```

### 5.4 Form Validation

```javascript
// src/js/modules/formValidation.js
export function initFormValidation() {
  const form = document.querySelector('#contact-form');
  if (!form) return;

  form.addEventListener('submit', async (e) => {
    e.preventDefault();

    const formData = new FormData(form);
    const errors = validateForm(formData);

    if (errors.length > 0) {
      displayErrors(errors);
      return;
    }

    await submitForm(formData);
  });
}
```

### 5.5 Scroll Animations

```javascript
// src/js/modules/animations.js
export function initAnimations() {
  const animateOnScroll = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('animate-in');
      }
    });
  }, {
    threshold: 0.1
  });

  document.querySelectorAll('[data-animate]').forEach(el => {
    animateOnScroll.observe(el);
  });
}
```

---

## 6. Image Optimization Strategy

### 6.1 Google Photos Integration

**11 Image URLs to Process**:
1. Download original images
2. Generate multiple sizes (thumbnail, small, medium, large)
3. Convert to modern formats (WebP, AVIF)
4. Create LQIP (Low Quality Image Placeholders)
5. Optimize with compression

**Size Variants**:
```javascript
const imageSizes = {
  thumbnail: { width: 150, quality: 80 },
  small: { width: 400, quality: 85 },
  medium: { width: 800, quality: 85 },
  large: { width: 1200, quality: 90 },
  xlarge: { width: 1920, quality: 90 }
};
```

### 6.2 Responsive Images

```html
<picture>
  <source
    type="image/avif"
    srcset="
      /assets/images/optimized/cafe-interior-400.avif 400w,
      /assets/images/optimized/cafe-interior-800.avif 800w,
      /assets/images/optimized/cafe-interior-1200.avif 1200w"
    sizes="(max-width: 640px) 400px, (max-width: 1024px) 800px, 1200px" />
  <source
    type="image/webp"
    srcset="
      /assets/images/optimized/cafe-interior-400.webp 400w,
      /assets/images/optimized/cafe-interior-800.webp 800w,
      /assets/images/optimized/cafe-interior-1200.webp 1200w"
    sizes="(max-width: 640px) 400px, (max-width: 1024px) 800px, 1200px" />
  <img
    src="/assets/images/optimized/cafe-interior-800.jpg"
    alt="Cozy interior of Leo's Coffee"
    loading="lazy"
    decoding="async" />
</picture>
```

### 6.3 Image Optimization Script

```javascript
// scripts/optimize-images.js
const sharp = require('sharp');
const fs = require('fs').promises;
const path = require('path');

const SIZES = [400, 800, 1200, 1920];
const FORMATS = ['webp', 'avif', 'jpeg'];

async function optimizeImage(inputPath, outputDir) {
  const filename = path.basename(inputPath, path.extname(inputPath));

  for (const size of SIZES) {
    for (const format of FORMATS) {
      const outputPath = path.join(
        outputDir,
        `${filename}-${size}.${format}`
      );

      await sharp(inputPath)
        .resize(size, null, { withoutEnlargement: true })
        .toFormat(format, { quality: 85 })
        .toFile(outputPath);
    }
  }

  // Generate LQIP
  const lqipPath = path.join(outputDir, `${filename}-lqip.jpg`);
  await sharp(inputPath)
    .resize(20)
    .blur(10)
    .toFile(lqipPath);
}
```

---

## 7. Performance Optimization

### 7.1 Critical Rendering Path

**Strategy**:
1. Inline critical CSS (above-the-fold)
2. Defer non-critical CSS
3. Preload key resources
4. Minimize render-blocking JavaScript

```html
<head>
  <!-- Preconnect to external domains -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

  <!-- Preload critical assets -->
  <link rel="preload" as="style" href="/src/css/main.css">
  <link rel="preload" as="font" type="font/woff2"
        href="/src/assets/fonts/inter-var.woff2" crossorigin>

  <!-- Critical CSS (inlined) -->
  <style>
    /* Critical above-the-fold styles */
  </style>

  <!-- Main stylesheet -->
  <link rel="stylesheet" href="/src/css/main.css">
</head>
```

### 7.2 Caching Strategy

**HTTP Headers** (via `.htaccess` or server config):
```apache
# Cache static assets for 1 year
<FilesMatch "\.(jpg|jpeg|png|gif|webp|avif|svg|ico|woff|woff2)$">
  Header set Cache-Control "max-age=31536000, public, immutable"
</FilesMatch>

# Cache CSS and JS for 1 month
<FilesMatch "\.(css|js)$">
  Header set Cache-Control "max-age=2592000, public"
</FilesMatch>

# HTML no cache
<FilesMatch "\.(html)$">
  Header set Cache-Control "max-age=0, no-cache, no-store, must-revalidate"
</FilesMatch>
```

### 7.3 Compression

```apache
# Enable Gzip compression
<IfModule mod_deflate.c>
  AddOutputFilterByType DEFLATE text/html text/plain text/xml text/css
  AddOutputFilterByType DEFLATE application/javascript application/json
  AddOutputFilterByType DEFLATE image/svg+xml
</IfModule>

# Enable Brotli (if available)
<IfModule mod_brotli.c>
  AddOutputFilterByType BROTLI_COMPRESS text/html text/plain text/xml text/css
  AddOutputFilterByType BROTLI_COMPRESS application/javascript application/json
</IfModule>
```

### 7.4 Performance Metrics Targets

| Metric | Target | Priority |
|--------|--------|----------|
| First Contentful Paint (FCP) | < 1.8s | High |
| Largest Contentful Paint (LCP) | < 2.5s | High |
| First Input Delay (FID) | < 100ms | High |
| Cumulative Layout Shift (CLS) | < 0.1 | High |
| Time to Interactive (TTI) | < 3.8s | Medium |
| Total Blocking Time (TBT) | < 200ms | Medium |
| Speed Index | < 3.4s | Medium |

---

## 8. SEO Strategy

### 8.1 Meta Tags

```html
<head>
  <!-- Primary Meta Tags -->
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Leo's Coffee - Café in Berlin Prenzlauer Berg | Kaffee, Tee & Frühstück</title>
  <meta name="description" content="Leo's Coffee in Berlin: Große Auswahl an Teesorten, exzellenter Kaffee, leckeres Frühstück. Perfekt zum Arbeiten am Laptop. Greifswalder Str. 2, 10405 Berlin.">
  <meta name="keywords" content="café berlin, kaffee berlin, tee berlin, frühstück berlin, laptop café, prenzlauer berg, greifswalder straße">
  <meta name="author" content="Leo's Coffee">
  <link rel="canonical" href="https://leoscoffee.berlin">

  <!-- Open Graph / Facebook -->
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://leoscoffee.berlin">
  <meta property="og:title" content="Leo's Coffee - Café in Berlin Prenzlauer Berg">
  <meta property="og:description" content="Große Auswahl an Teesorten, exzellenter Kaffee, leckeres Frühstück. Perfekt zum Arbeiten.">
  <meta property="og:image" content="https://leoscoffee.berlin/assets/images/og-image.jpg">
  <meta property="og:locale" content="de_DE">

  <!-- Twitter -->
  <meta property="twitter:card" content="summary_large_image">
  <meta property="twitter:url" content="https://leoscoffee.berlin">
  <meta property="twitter:title" content="Leo's Coffee - Café in Berlin Prenzlauer Berg">
  <meta property="twitter:description" content="Große Auswahl an Teesorten, exzellenter Kaffee, leckeres Frühstück.">
  <meta property="twitter:image" content="https://leoscoffee.berlin/assets/images/twitter-image.jpg">

  <!-- Favicon -->
  <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
  <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
</head>
```

### 8.2 Schema.org Structured Data

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "CafeOrCoffeeShop",
  "name": "Leo's Coffee",
  "image": [
    "https://leoscoffee.berlin/assets/images/cafe-exterior.jpg",
    "https://leoscoffee.berlin/assets/images/cafe-interior.jpg"
  ],
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Greifswalder Str. 2",
    "addressLocality": "Berlin",
    "postalCode": "10405",
    "addressCountry": "DE"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 52.5328,
    "longitude": 13.4213
  },
  "url": "https://leoscoffee.berlin",
  "telephone": "+49-30-XXXXXXXX",
  "servesCuisine": ["Coffee", "Tea", "Breakfast"],
  "priceRange": "$$",
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "08:00",
      "closes": "18:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Saturday", "Sunday"],
      "opens": "09:00",
      "closes": "19:00"
    }
  ],
  "amenityFeature": [
    {
      "@type": "LocationFeatureSpecification",
      "name": "Free WiFi",
      "value": true
    },
    {
      "@type": "LocationFeatureSpecification",
      "name": "Laptop Friendly",
      "value": true
    }
  ],
  "menu": "https://leoscoffee.berlin/#menu",
  "acceptsReservations": false
}
</script>
```

### 8.3 Sitemap Structure

```xml
<!-- sitemap.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://leoscoffee.berlin/</loc>
    <lastmod>2025-10-24</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://leoscoffee.berlin/#about</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://leoscoffee.berlin/#menu</loc>
    <changefreq>weekly</changefreq>
    <priority>0.9</priority>
  </url>
</urlset>
```

---

## 9. Accessibility (WCAG 2.1 AA)

### 9.1 Compliance Checklist

**Perceivable**:
- [ ] All images have meaningful alt text
- [ ] Color contrast ratio ≥ 4.5:1 for normal text
- [ ] Color contrast ratio ≥ 3:1 for large text
- [ ] Content doesn't rely solely on color
- [ ] Text can be resized up to 200%
- [ ] Proper heading hierarchy (h1 → h2 → h3)

**Operable**:
- [ ] All functionality available via keyboard
- [ ] Focus indicators visible
- [ ] No keyboard traps
- [ ] Skip navigation link provided
- [ ] Page titles descriptive
- [ ] Link purposes clear from text

**Understandable**:
- [ ] Language of page declared (`lang="de"`)
- [ ] Consistent navigation
- [ ] Form labels and error messages clear
- [ ] Help text provided for forms

**Robust**:
- [ ] Valid HTML5
- [ ] ARIA landmarks used correctly
- [ ] Compatible with assistive technologies

### 9.2 ARIA Landmarks

```html
<header role="banner">
  <nav role="navigation" aria-label="Main navigation">
    <!-- Navigation -->
  </nav>
</header>

<main role="main">
  <section aria-labelledby="hero-heading">
    <!-- Content -->
  </section>
</main>

<footer role="contentinfo">
  <!-- Footer -->
</footer>
```

### 9.3 Keyboard Navigation

```javascript
// src/js/modules/navigation.js
export function initNavigation() {
  const nav = document.querySelector('nav');
  const menuButton = document.querySelector('[data-menu-toggle]');

  // Trap focus in mobile menu when open
  menuButton.addEventListener('click', () => {
    const isOpen = nav.getAttribute('aria-expanded') === 'true';
    nav.setAttribute('aria-expanded', !isOpen);

    if (!isOpen) {
      trapFocus(nav);
    }
  });

  // Escape key closes menu
  document.addEventListener('keydown', (e) => {
    if (e.key === 'Escape') {
      nav.setAttribute('aria-expanded', 'false');
    }
  });
}
```

---

## 10. Implementation Plan

### Phase 1: Foundation (Week 1)
**Tasks**:
1. Set up folder structure
2. Create design system (CSS variables)
3. Implement base HTML structure
4. Set up build/optimization scripts
5. Download and optimize images from Google Photos

**Deliverables**:
- Complete folder structure
- `src/css/base/variables.css`
- `src/css/base/reset.css`
- `src/css/base/typography.css`
- `index.html` skeleton
- Image optimization script

### Phase 2: Layout & Components (Week 1-2)
**Tasks**:
1. Build responsive navigation
2. Implement grid system
3. Create reusable components (buttons, cards)
4. Develop hero section
5. Build about section

**Deliverables**:
- `src/css/layout/header.css`
- `src/css/components/*.css`
- `src/js/modules/navigation.js`
- Hero and About sections complete

### Phase 3: Content Sections (Week 2)
**Tasks**:
1. Menu section with categories (Coffee, Tea, Breakfast)
2. Gallery integration with lightbox
3. Features section (laptop-friendly highlights)
4. Reviews section with testimonials
5. Location section with embedded map

**Deliverables**:
- `src/css/sections/*.css`
- `src/js/modules/gallery.js`
- All content sections complete

### Phase 4: Interactivity (Week 2-3)
**Tasks**:
1. Implement lazy loading
2. Add scroll animations
3. Build contact form with validation
4. Mobile navigation functionality
5. Smooth scrolling

**Deliverables**:
- `src/js/modules/lazyLoad.js`
- `src/js/modules/animations.js`
- `src/js/modules/formValidation.js`
- `src/js/modules/smoothScroll.js`

### Phase 5: Optimization & Testing (Week 3)
**Tasks**:
1. Performance optimization (minification, compression)
2. SEO implementation (meta tags, schema.org)
3. Accessibility audit and fixes
4. Cross-browser testing
5. Mobile device testing

**Deliverables**:
- Lighthouse score > 90 for all categories
- WCAG 2.1 AA compliance
- All browsers tested (Chrome, Firefox, Safari, Edge)

### Phase 6: Deployment (Week 3-4)
**Tasks**:
1. Set up hosting
2. Configure server (caching, compression)
3. SSL certificate installation
4. DNS configuration
5. Submit sitemap to search engines

**Deliverables**:
- Live website at production URL
- Google Search Console verification
- Analytics implementation

---

## 11. Technology Stack Decisions

### 11.1 Why Vanilla JavaScript?

**Rationale**:
- **Performance**: No framework overhead (~50KB+ savings)
- **Simplicity**: Single-page website doesn't need complex state management
- **Load Time**: Faster initial page load
- **Maintenance**: No dependency updates required
- **Learning**: Better understanding of web fundamentals

**Trade-offs**:
- More manual DOM manipulation
- No built-in reactivity
- Custom event handling needed

**Decision**: ✅ Vanilla JS is optimal for this project size

### 11.2 CSS Approach

**Considered Options**:
1. **Vanilla CSS** (Selected)
2. Tailwind CSS
3. CSS-in-JS
4. SCSS/SASS

**Rationale for Vanilla CSS**:
- Modern CSS features (Grid, Flexbox, Custom Properties) are sufficient
- No build step required
- Smaller file sizes
- Better browser caching
- CSS Cascade benefits for theming

**Enhancement**: CSS Custom Properties for design system

### 11.3 Build Tools

**Decision**: Minimal build process
- Image optimization script (Node.js)
- CSS/JS minification (optional, for production)
- No complex bundler needed

**Rationale**:
- Simple project scope
- HTTP/2 makes bundling less critical
- Easier debugging in development

---

## 12. Design System Tokens

### 12.1 Animation Tokens

```css
:root {
  /* Durations */
  --duration-instant: 100ms;
  --duration-fast: 200ms;
  --duration-base: 300ms;
  --duration-slow: 500ms;
  --duration-slower: 700ms;

  /* Easings */
  --ease-in: cubic-bezier(0.4, 0, 1, 1);
  --ease-out: cubic-bezier(0, 0, 0.2, 1);
  --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

### 12.2 Micro-interactions

```css
/* Button hover effect */
.btn {
  transform: translateY(0);
  transition: transform var(--duration-base) var(--ease-out),
              box-shadow var(--duration-base) var(--ease-out);
}

.btn:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}

/* Card reveal animation */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.card[data-animate] {
  animation: fadeInUp var(--duration-slow) var(--ease-out) forwards;
}
```

---

## 13. Security Considerations

### 13.1 Content Security Policy

```html
<meta http-equiv="Content-Security-Policy"
      content="
        default-src 'self';
        script-src 'self' 'unsafe-inline';
        style-src 'self' 'unsafe-inline' fonts.googleapis.com;
        font-src 'self' fonts.gstatic.com;
        img-src 'self' data: https:;
        connect-src 'self';
      ">
```

### 13.2 Form Security

```javascript
// XSS Prevention
function sanitizeInput(input) {
  const div = document.createElement('div');
  div.textContent = input;
  return div.innerHTML;
}

// Email validation
function isValidEmail(email) {
  const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return re.test(email);
}
```

---

## 14. Monitoring & Analytics

### 14.1 Performance Monitoring

```javascript
// Web Vitals tracking
import {getCLS, getFID, getFCP, getLCP, getTTFB} from 'web-vitals';

function sendToAnalytics(metric) {
  // Send to analytics endpoint
  console.log(metric);
}

getCLS(sendToAnalytics);
getFID(sendToAnalytics);
getFCP(sendToAnalytics);
getLCP(sendToAnalytics);
getTTFB(sendToAnalytics);
```

### 14.2 Error Tracking

```javascript
window.addEventListener('error', (event) => {
  // Log error to monitoring service
  console.error('Global error:', event.error);
});

window.addEventListener('unhandledrejection', (event) => {
  // Log promise rejection
  console.error('Unhandled promise rejection:', event.reason);
});
```

---

## 15. Future Enhancements

### 15.1 Progressive Web App (PWA)

**Considerations**:
- Service Worker for offline functionality
- Web App Manifest
- Push notifications for specials

### 15.2 Online Ordering Integration

**Potential Features**:
- Menu ordering system
- Payment integration
- Pickup time selection

### 15.3 Internationalization

**Languages**:
- German (primary)
- English (secondary)
- Other languages as needed

---

## 16. Deployment Checklist

### Pre-Deployment
- [ ] All images optimized
- [ ] CSS/JS minified
- [ ] HTML validated
- [ ] Accessibility tested
- [ ] Cross-browser tested
- [ ] Mobile responsive verified
- [ ] Forms tested
- [ ] SEO meta tags complete
- [ ] Schema.org markup verified
- [ ] Sitemap generated
- [ ] robots.txt created
- [ ] Favicon set

### Deployment
- [ ] Server configured (caching, compression)
- [ ] SSL certificate installed
- [ ] DNS configured
- [ ] 301 redirects set up (if needed)
- [ ] Analytics installed
- [ ] Error pages (404, 500) customized

### Post-Deployment
- [ ] Google Search Console verification
- [ ] Submit sitemap to search engines
- [ ] Test live site (all features)
- [ ] Monitor performance metrics
- [ ] Set up uptime monitoring

---

## 17. File Size Budget

| Resource Type | Target Size | Max Size |
|---------------|-------------|----------|
| HTML (initial) | < 15KB | 20KB |
| CSS (total) | < 30KB | 50KB |
| JS (total) | < 40KB | 60KB |
| Images (hero) | < 150KB | 200KB |
| Images (gallery, each) | < 100KB | 150KB |
| Total Page Weight | < 500KB | 750KB |

---

## 18. Browser Support

**Target Browsers**:
- Chrome/Edge (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)
- iOS Safari (last 2 versions)
- Samsung Internet (last 2 versions)

**Graceful Degradation**:
- CSS Grid with Flexbox fallback
- WebP/AVIF with JPEG fallback
- Modern JavaScript with polyfills for older browsers (if needed)

---

## Architecture Decision Records (ADRs)

### ADR-001: Use Vanilla JavaScript Over React
**Status**: Accepted
**Context**: Need to choose frontend framework
**Decision**: Use Vanilla JavaScript
**Consequences**:
- Positive: Better performance, simpler deployment, no build complexity
- Negative: More manual DOM work, no component reusability framework

### ADR-002: Mobile-First Responsive Design
**Status**: Accepted
**Context**: Support all device sizes
**Decision**: Build mobile-first, progressively enhance
**Consequences**:
- Positive: Better mobile UX, progressive enhancement
- Negative: May require more CSS media queries

### ADR-003: CSS Custom Properties for Design System
**Status**: Accepted
**Context**: Need consistent theming
**Decision**: Use CSS Custom Properties (CSS Variables)
**Consequences**:
- Positive: Runtime theme changes, better maintainability
- Negative: Limited IE11 support (acceptable trade-off)

---

**Document Version**: 1.0
**Last Updated**: 2025-10-24
**Author**: System Architecture Designer
**Review Status**: Ready for Implementation
