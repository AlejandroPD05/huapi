# Huapi — carta digital

Carta de restaurante pensada para leerse en el móvil desde un QR: tres
categorías, 14 platos con precio, descripción y etiquetas, y una barra de
pestañas que se resalta sola según la sección visible.

**▶ Ver en vivo:** https://alejandropd05.github.io/huapi/

## Stack

HTML semántico + CSS con variables de diseño + 34 líneas de JavaScript. Sin
dependencias, sin build.

## Cómo funciona

- Cada pestaña es un `<a href="#id">`: **funciona aunque falle el JS**
  (degradación elegante por anclas nativas).
- Dos `IntersectionObserver`:
  - marca la pestaña activa (`rootMargin: '-40% 0px -50% 0px'`),
  - alterna la sombra `is-stuck` de la barra fija.
- `scroll-margin-top: 64px` evita que los anclajes queden tapados por la barra.

## Detalles de accesibilidad

- `lang="es"`, landmarks (`header`/`nav`/`main`/`footer`)
- SVG decorativo con `aria-hidden="true"`
- `prefers-reduced-motion` desactiva animaciones y scroll suave
- Etiquetas de plato con contraste AA

## Estructura

```
index.html    Semántica, categorías y platos
style.css     Tokens (:root), BEM, mobile-first (max-width 480px)
script.js     Los dos observers, desacoplados vía data-target/data-category
```

## Posibles mejoras

- `aria-current` en la pestaña activa y `aria-label` en el `<nav>`
- Datos estructurados JSON-LD (`schema.org/Menu`) para rich results
- Filtro por etiquetas (sin gluten / vegetariano / picante)
