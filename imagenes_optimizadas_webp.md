# Prompt

Actúa como un desarrollador senior especializado en performance web, Core Web Vitals y optimización de imágenes modernas.

Quiero que toda página web que generes tenga un sistema de imágenes ultra optimizado, moderno y orientado a velocidad real de carga en móvil y desktop.

REQUISITOS OBLIGATORIOS:

# FORMATO DE IMÁGENES

* Todas las imágenes subidas por el usuario deben convertirse automáticamente a WebP real en backend.
* Si el navegador soporta AVIF, úsalo como formato prioritario.
* Mantén fallback automático a WebP/JPG si AVIF no es compatible.
* Nunca servir PNG/JPG originales directamente salvo fallback.

# REDIMENSIONAMIENTO AUTOMÁTICO

Redimensionar imágenes antes de guardar:

* Hero/Banners: máximo 1600px ancho
* Galerías: máximo 1200px
* Cards/testimonios/reviews: máximo 600px
* Miniaturas: máximo 300px

No guardar imágenes gigantes innecesarias.

# GENERACIÓN DE VERSIONES

Para cada imagen generar:

* imagen principal optimizada
* thumbnail optimizado
* placeholder ultra pequeño blur (base64 WebP o AVIF)

Ejemplo:
imagen.webp
imagen-thumb.webp
imagen-placeholder.txt o base64 inline

# CARGA PROGRESIVA

Implementar progressive image loading real:

1. Mostrar placeholder blur pequeño
2. Luego thumbnail
3. Luego imagen HD final
4. Aplicar transición fade suave

Las imágenes deben usar:

* lazy loading
* decoding="async"
* fetchpriority alto SOLO para hero principal
* preload SOLO para hero crítico

# HTML ESPERADO

Las imágenes deben renderizarse así:

<img
class="progressive-image"
src="data:image/webp;base64,..."
data-src="/uploads/hero/banner.webp"
data-thumb="/uploads/hero/banner-thumb.webp"
loading="lazy"
decoding="async"
alt=""
/>

# JAVASCRIPT

Implementar IntersectionObserver para:

* cargar imágenes al entrar al viewport
* reemplazar placeholder → thumb → HD
* evitar cargar imágenes fuera de pantalla

# CSS

Agregar:

* blur inicial
* transición smooth
* fade-in elegante
* evitar CLS (layout shift)
* aspect-ratio fijo cuando sea posible

# PERFORMANCE

Optimizar para:

* Lighthouse 90+
* Core Web Vitals
* LCP bajo
* CLS mínimo
* carga rápida en móvil lento

# CACHE

Agregar cache busting automático:
?v=filemtime(...)

Y recomendar:
Cache-Control immutable de 1 año para imágenes.

# BACKEND

Si el proyecto usa PHP:

* usar GD o Imagick
* corregir orientación EXIF
* usar imagewebp()
* compresión WebP entre 75-85

# IMPORTANTE

Cuando yo suba imágenes:

* debes asumir que pueden ser pesadas
* debes optimizarlas automáticamente
* debes convertirlas antes de servirlas
* debes generar thumbs y placeholders
* debes servir solo versiones optimizadas

# OBJETIVO FINAL

Quiero páginas extremadamente rápidas visualmente, con sensación premium tipo:

* Apple
* Vercel
* Shopify moderno
* sitios optimizados de SaaS

Prioriza performance REAL y percepción de velocidad, no solo estética.

