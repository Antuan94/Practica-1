# Design Spec — The Chosen · Boilerplate Web

> Especificación de diseño para agentes de IA (generación de UI, prototipos y
> revisión de consistencia). Basada en la guía de boilerplate web solicitada:
> HTML + CSS propios, flexbox como pilar, Normalize, divs semánticos,
> contenedor variable de 1000–2000 px, Google Fonts, Font Awesome, variables
> globales en `:root`, `position: fixed` en esquina inferior derecha, unidades
> absolutas para el diseño general y relativas para los elementos específicos,
> menú estilo css3-menu-generator, footer con redes sociales, contenido con
> artículos repetidos.

## 1. Brief y objetivo

- **Proyecto**: Boilerplate de página web.
- **Tema**: Serie *The Chosen* (historia de Jesús y sus discípulos).
- **Estética**: Estilo *paneles de manga* (marcas, halftone, siluetas, acentos).
- **Función**: Estructura inicial de un sitio (Header / Main / Nav / Aside /
  Footer) con primera capa de divs semánticos y hero + episodios + sidebar.

## 2. Paleta de color

| Variable | Hex | Uso |
|---|---|---|
| `--color-ink` | `#151218` | Fondo principal oscuro, textos sobre papel, header/footer |
| `--color-papel` | `#f8f3e9` | Fondo de tarjetas, paneles, textos sobre oscuro |
| `--color-rojo` | `#c8102e` | Acento principal (CTAs, paneles destacados, bordes manga) |
| `--color-rojo-oscuro` | `#9b0c24` | Hover/focus del acento |
| `--color-gris` | `#5c5a63` | Texto secundario |

**Regla**: contraste mínimo 4.5:1 para texto; el acento rojo se reserva para
interacción y énfasis (nunca texto largo sobre fondo claro).

## 3. Tipografía

- **Titulares**: `Cinzel` (Google Fonts, pesos 500/600/700) — registro épico.
- **Cuerpo**: `Roboto` (Google Fonts, 400/500/700).
- **Paneles / captions**: `Courier New` fallback (estilo editorial de revista).

Escala (base `1rem = 16px`):

| Variable | Tamaño | Uso |
|---|---|---|
| `--texto-xs` | 0.8rem | Meta, panel-label, captions |
| `--texto-sm` | 0.9rem | Nav, botones pequeños |
| `--texto-md` | 1rem | Cuerpo |
| `--texto-lg` | 1.25rem | Subtítulos |
| `--texto-xl` | 1.75rem | Artículo destacado |
| `--texto-2xl` | 2.5rem | Sección |
| `--texto-3xl` | 3.5rem | Hero |

## 4. Unidades y escala

- **Diseño general**: unidades absolutas (`px`) — contenedor (`min(100%, 2000px)`),
  anchos de aside (`340px`), sombras offset tipo cómic.
- **Elementos específicos**: unidades relativas (`rem`/`em`) — tipografía,
  espaciado de componentes, paddings.
- Contenedor central: variable entre **1000 px y 2000 px** (`--ancho-contenedor-max`).

## 5. Layout

- **Pilar**: Flexbox (`display: flex`) para header, contenido split
  (main + aside), footer.
- **Frame de contenido**: CSS Grid (`grid-template-columns: repeat(6, 1fr)`) con
  artículos que ocupan `span 2` (o `span 4` destacado).
- Hero: grid de 2 columnas (texto + panel).
- Breakpoints: 1024 px, 980 px, 820 px, 620 px, 480 px.

## 6. Componentes

| Componente | Detalle |
|---|---|
| Header | `#menu-switch` + label checkbox hack + `.nav` (dropdown en móvil) |
| Menú | Generador css3-menu: `.css3menu`, `.css3menu-item`, `.css3menu-submenu` |
| Hero | `.hero`, `.panel`, `.panel-hero`, `.panel-label` |
| Artículos | `.grid-paneles`, `.articulo`, `.articulo--destacado` |
| Aside | `.sidebar`, `.widget`, `.newsletter` |
| Footer | `.site-footer`, `.footer-contenido`, `.redes-sociales` |
| Fijo | `.ir-arriba` (`position: fixed`, esquina inferior derecha) |
| Accesibilidad | Skip link, `.sr-only`, `:focus-visible`, `prefers-reduced-motion` |

## 7. Iconografía e imágenes

- **Iconos**: Font Awesome 6 via CDN (`cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/`).
- **Fuentes**: Google Fonts (`Cinzel`, `Roboto`, `display=swap`).
- **Imágenes**: SVG locales en `assets/img/` con estilo de panel de manga
  (halftone, siluetas, acento). Toda imagen lleva atributo `alt` descriptivo.

## 8. Interacciones

- Submenús: `:hover` y `:focus-within`.
- Móvil: checkbox hack `#menu-switch:checked ~ .nav`.
- Artículos destacados: hover con borde rojo + sombra offset estilo cómic
  (`box-shadow: 10px 10px 0 rgba(200,16,46,.85)`).
- Botón flotante: ancla `href="#inicio"`.

## 9. Guía para agentes IA de diseño

1. Mantener el lenguaje visual: halftone, siluetas, borde grueso de panel,
   acento bermellón sobre ink/paper.
2. No introducir otras fuentes o iconos fuera de los CDNs indicados.
3. Respetar la escala tipográfica y la escala de spacing (`--espacio-*`).
4. Mantener el menú dentro del patrón css3-menu generado.
5. Container siempre `min(100%, 2000px)`.
6. Todo texto nuevo debe respetar contraste y usar `alt` en imágenes.
7. Revisar que el layout siga usando flexbox para ubicación y grid solo para
   paneles de contenido.

## 10. Estado actual del boilerplate

- Estructura semántica inicial: Header / Main / Nav / Aside / Footer.
- Hero + listado de artículos + sidebar con widgets.
- Footer con iconos de redes sociales (Font Awesome).
- Botón fijo en esquina inferior derecha.
