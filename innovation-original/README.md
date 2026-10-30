# Innovation Emotion · Landing page responsive

Réplica del diseño de Figma **#22 – innovationEmotion**, hecha para el **Examen del Progreso 1** de la materia **Ingeniería Web**.

Es una sola pantalla, construida con **HTML semántico** y **Sass**, aplicando **Flexbox**, **CSS Grid**, **media queries (mobile-first)** y la nomenclatura **BEM**. No usa JavaScript: el slideshow está hecho solo con CSS.

| Escritorio | Celular |
|---|---|
| ![Vista de escritorio](docs/escritorio.jpg) | ![Vista de celular](docs/celular.jpg) |

---

## Tecnologías

- **HTML5**: etiquetas semánticas (`header`, `nav`, `main`, `section`, `article`, `form`, `footer`).
- **Sass (SCSS)**: variables, nesting, mixins y parciales (un archivo por componente).
- **CSS**: Flexbox, CSS Grid, media queries y animaciones con `@keyframes`.
- **Google Fonts**: Rubik, Abel y Open Sans.

## Cómo verlo en tu computadora

1. Clona el repositorio o descárgalo como ZIP.
2. Ábrelo en **Visual Studio Code**.
3. Instala las extensiones **Live Server** y **Live Sass Compiler**.
4. Clic en **Watch Sass** (compila `scss/main.scss` en `scss/main.css`).
5. Clic en **Go Live** para abrir la página en el navegador.

> El archivo `scss/main.css` ya viene compilado, así que también basta con abrir `index.html`.

## Estructura del proyecto

```
├── index.html            ← estructura y contenido (HTML)
├── images/               ← imágenes exportadas del Figma
├── docs/                 ← capturas para este README
└── scss/
    ├── main.scss         ← archivo principal: solo junta los parciales con @use
    ├── main.css          ← CSS generado (no se edita a mano)
    ├── _variables.scss   ← colores, fuentes y puntos de quiebre
    ├── _mixins.scss      ← mixins: sombra() y slideshow()
    ├── _base.scss        ← reset, body, img responsive, .contenedor, .parrafo
    ├── _boton.scss       ← componente botón
    ├── _titulo.scss      ← componente título con rayita azul
    ├── _menu.scss        ← componente menú (se usa en header y footer)
    ├── _header.scss      ← cabecera: logo, menú y portada
    ├── _ventajas.scss    ← 4 tarjetas con ícono
    ├── _info.scss        ← bloques imagen + texto (About, Be unique, Products)
    ├── _slider.scss      ← slideshow solo con CSS
    ├── _habilidades.scss ← texto + barras de porcentaje
    ├── _banner.scss      ← franja "Unique experiences"
    ├── _clientes.scss    ← logos de clientes
    ├── _servicios.scss   ← 3 tarjetas de servicios
    ├── _soporte.scss     ← formulario de contacto
    └── _footer.scss      ← pie de página
```

## Técnicas aplicadas

### Flexbox (acomodar en una dirección)
| Sección | Uso |
|---|---|
| Header | Logo y menú: `column` en celular → `row` + `space-between` en escritorio |
| Menú | Enlaces en fila con `flex-wrap: wrap` |
| Info (About, Be unique, Products) | Imagen y texto: `column` → `row`; el modificador `info--invertido` usa `row-reverse` |
| Clientes | Logos con `flex-wrap` y `space-between` |
| Footer | Datos de contacto: `column` → `row` |
| Slideshow | La "tira" de fotos en fila |

### CSS Grid (filas y columnas)
| Sección | Uso |
|---|---|
| Ventajas | `repeat(2, 1fr)` en celular → `repeat(4, 1fr)` en escritorio |
| Habilidades | 1 columna → `1fr 1.3fr` |
| Servicios | 1 columna → `repeat(3, 1fr)` |
| Formulario | 3 columnas; el mensaje ocupa todo el ancho con `grid-column: 1 / -1` |

### Sass
- **Variables** (`_variables.scss`): `$azul`, `$negro`, `$fuente-titulos`, `$tablet: 768px`, `$desktop: 1024px`…
- **Nesting** con `&`: `&__elemento`, `&--modificador`, `&:hover`.
- **Mixins** (`_mixins.scss`):
  - `sombra($color)`: sombra de color para las tarjetas.
  - `slideshow($tiempo)`: todo el slideshow en un mixin; se usa con `@include slideshow(6s)`.
- **Parciales / componentes**: cada sección y componente en su propio archivo `_nombre.scss`, unidos en `main.scss` con `@use`.

### Media queries (mobile-first)
Los estilos base son para celular. Con `@media (min-width: $tablet)` y `@media (min-width: $desktop)` se ajusta el diseño para tablet y escritorio.

| Punto de quiebre | Ancho |
|---|---|
| `$tablet` | 768px |
| `$desktop` | 1024px |

### BEM (Bloque · Elemento · Modificador)
```html
<article class="servicio servicio--azul">       <!-- bloque + modificador -->
  <img class="servicio__icono" ...>              <!-- elemento -->
  <h3 class="servicio__titulo">Easy import</h3>  <!-- elemento -->
</article>
```

## Retos del examen implementados

- **Títulos centrados**: modificador `titulo--centrado`, que ocupa su propia fila (`flex-basis: 100%` / `grid-column: 1 / -1`) con `text-align: center`.
- **Slideshow solo con CSS hecho con un mixin**: en la sección *About us*, 2 fotos que se alternan para siempre usando `overflow: hidden`, una tira con `display: flex` y una animación `@keyframes` con `transform: translateX()`.

## Autor

**Adrián** · Ingeniería Web · 7.º semestre
