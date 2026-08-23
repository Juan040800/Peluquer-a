# SEDA STUDIO — Sitio web

Landing page de una sola página para un salón de belleza para mujeres, estética pastel/femenina con efecto "liquid glass". Archivo único: `seda-studio.html`.

## Cómo verlo

Abre `seda-studio.html` directamente en el navegador. HTML, CSS y JS están en un solo archivo — no necesita servidor ni build.

## Estructura de secciones

1. **Header** — logo, nav con menú móvil funcional (hamburguesa con animación), botón "Reservar". El fondo del header pasa a vidrio esmerilado (`liquid-glass`) al hacer scroll.
2. **Hero** (`.hero`) — cinta de seda animada en SVG de fondo (3 trazos con distinto grosor/velocidad), barra de búsqueda flotante estilo glass (Servicio/Estilista/Sede/Fecha) y dos tarjetas flotantes con efecto tilt 3D al mover el mouse: "Reserva tu lugar" y "Balayage + Tratamiento".
3. **Servicios** (`#servicios`) — 3 tarjetas: Corte de Autor, Balayage & Matiz, Ritual Seda.
4. **Estudio** (`#estudio`) — panel oscuro con galería de 3 fotos en arco (Sala principal, Estación de color, Sala de descanso), con tilt 3D al pasar el mouse.
5. **Productos** (`#productos`) — 4 productos con botón "+" para agregar.

## ⚠️ Pendiente antes de publicar

- **El archivo llega incompleto**: no tiene sección de testimonios, CTA final ni **footer** — la página termina abruptamente después de Productos. Hace falta agregar esas piezas (o confirmar si nunca existieron en el diseño original).
- **Las fotos usan URLs de Unsplash sin verificar** (`images.unsplash.com/photo-...`). En el proyecto de la barbería tuvimos IDs de foto inventados que no cargaban ni con internet real — conviene revisar cada una antes de publicar, o reemplazarlas por fotos reales del salón.
- El botón "Reservar" y la barra de búsqueda son de interfaz únicamente; no están conectados a ningún backend de reservas todavía.

## Personalización rápida

Colores centralizados en `:root`:

```css
--cream, --cream-2   /* fondo cálido */
--blush              /* rosa suave */
--rose, --rose-dark  /* acento principal */
--ink                /* texto, malva oscuro */
--gold               /* detalles dorados */
```

## Tipografías

- **Cormorant Garamond** — titulares y acentos en cursiva.
- **Jost** — texto de cuerpo y UI.

## Detalles técnicos / accesibilidad

- `.liquid-glass` es la única "receta" de vidrio esmerilado reutilizada en todo el sitio (header, barra de búsqueda, tarjetas flotantes, menú móvil) para que se vea consistente.
- Respeta `prefers-reduced-motion` (desactiva animaciones de la cinta, el tilt 3D y el reveal-on-scroll) y `prefers-reduced-transparency` (quita el blur y usa fondo sólido).
- Incluye skip-link para navegación por teclado y `aria-label`/`aria-expanded` en el menú móvil.
- El scroll-reveal de las tarjetas usa `IntersectionObserver`; si el navegador no lo soporta, el contenido se muestra directo sin animación.
