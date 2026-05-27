# HTML Deck Architecture

Every deck is a single HTML file with inline CSS and JavaScript.

## Required Structure

```html
<!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Presentation Title</title>
  <style>
    /* Reset, stage CSS, chosen preset CSS, slide layouts */
  </style>
</head>
<body>
  <main class="deck-viewport" aria-label="Presentation">
    <section class="deck-stage" id="deckStage">
      <article class="slide active" data-slide="1">
        <!-- fixed 1920x1080 slide content -->
      </article>
    </section>
  </main>
  <div class="deck-ui" aria-hidden="false">
    <div class="progress" id="progress"></div>
    <div class="counter" id="counter">1 / 1</div>
  </div>
  <script>
    /* slide controller */
  </script>
</body>
</html>
```

## Mandatory Stage CSS

```css
* { box-sizing: border-box; }
html, body {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
}
body {
  font-family: var(--font-cn);
  background: #111;
}
.deck-viewport {
  position: fixed;
  inset: 0;
  overflow: hidden;
}
.deck-stage {
  position: absolute;
  left: 0;
  top: 0;
  width: 1920px;
  height: 1080px;
  transform-origin: top left;
  overflow: hidden;
}
.slide {
  position: absolute;
  inset: 0;
  width: 1920px;
  height: 1080px;
  overflow: hidden;
  isolation: isolate;
  visibility: hidden;
  opacity: 0;
  pointer-events: none;
  transition: opacity 420ms ease, visibility 420ms ease;
}
.bg-layer {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}
.content-layer {
  position: relative;
  z-index: 2;
}
.chrome-layer {
  position: absolute;
  inset: 0;
  z-index: 3;
  pointer-events: none;
}
.slide.active {
  visibility: visible;
  opacity: 1;
  pointer-events: auto;
}
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 1ms !important;
    transition-duration: 1ms !important;
    scroll-behavior: auto !important;
  }
}
```

Do not switch slides using `display: none` / `display: block`; later slide layout classes can override display and show every slide at once.

## Required JavaScript Features

Include a small controller with:

- stage scaling based on `visualViewport` when available, falling back to `window.innerWidth/innerHeight`
- keyboard navigation: `ArrowRight`, `ArrowDown`, `Space`, `PageDown`, `ArrowLeft`, `ArrowUp`, `PageUp`, `Home`, `End`
- touch swipe navigation
- wheel navigation with debounce
- progress bar and counter updates
- hash support if useful, such as `#3`

Use this controller shape:

```javascript
class SlideDeck {
  constructor() {
    this.stage = document.getElementById('deckStage');
    this.slides = [...document.querySelectorAll('.slide')];
    this.index = 0;
    this.bind();
    this.scale();
    this.show(0);
  }
  scale() {
    const viewport = window.visualViewport || window;
    const width = viewport.width || window.innerWidth;
    const height = viewport.height || window.innerHeight;
    const scale = Math.min(width / 1920, height / 1080);
    const left = Math.max(0, (width - 1920 * scale) / 2);
    const top = Math.max(0, (height - 1080 * scale) / 2);
    this.stage.style.transform = `scale(${scale})`;
    this.stage.style.left = `${left}px`;
    this.stage.style.top = `${top}px`;
  }
  show(index) {
    this.index = Math.max(0, Math.min(index, this.slides.length - 1));
    this.slides.forEach((slide, i) => slide.classList.toggle('active', i === this.index));
    const counter = document.getElementById('counter');
    const progress = document.getElementById('progress');
    if (counter) counter.textContent = `${this.index + 1} / ${this.slides.length}`;
    if (progress) progress.style.transform = `scaleX(${(this.index + 1) / this.slides.length})`;
  }
  next() { this.show(this.index + 1); }
  prev() { this.show(this.index - 1); }
  bind() {
    window.addEventListener('resize', () => this.scale());
    window.visualViewport?.addEventListener('resize', () => this.scale());
    window.visualViewport?.addEventListener('scroll', () => this.scale());
    document.addEventListener('keydown', (event) => {
      if (event.target?.isContentEditable) return;
      const next = ['ArrowRight', 'ArrowDown', ' ', 'PageDown'];
      const prev = ['ArrowLeft', 'ArrowUp', 'PageUp'];
      if (next.includes(event.key)) { event.preventDefault(); this.next(); }
      if (prev.includes(event.key)) { event.preventDefault(); this.prev(); }
      if (event.key === 'Home') this.show(0);
      if (event.key === 'End') this.show(this.slides.length - 1);
    });
    let startX = 0;
    window.addEventListener('touchstart', (event) => { startX = event.touches[0].clientX; }, { passive: true });
    window.addEventListener('touchend', (event) => {
      const dx = event.changedTouches[0].clientX - startX;
      if (Math.abs(dx) > 50) dx < 0 ? this.next() : this.prev();
    }, { passive: true });
    let wheelLock = false;
    window.addEventListener('wheel', (event) => {
      if (wheelLock || Math.abs(event.deltaY) < 24) return;
      wheelLock = true;
      event.deltaY > 0 ? this.next() : this.prev();
      setTimeout(() => { wheelLock = false; }, 450);
    }, { passive: true });
  }
}
new SlideDeck();
```

## Layout Patterns

Include only layouts that the deck uses:

- cover
- agenda
- section divider
- key message
- two-column explanation
- metric/data page
- table/matrix
- timeline/roadmap
- quote or mission page
- closing page

Avoid nested cards. For high-density pages, prefer grid regions and fine rules over stacked decorative cards.

## Layering And Spacing

Read `layout-safety.md` before composing CSS. Use `.bg-layer`, `.content-layer`, and `.chrome-layer` consistently:

- decorative dot fields, giant letters, geometric shapes, quote marks, and texture charts go in `.bg-layer`
- real text, UI mockups, charts, tables, metrics, and cards go in `.content-layer`
- page numbers, deck labels, and progress UI go in `.chrome-layer`

Do not use a high `z-index` to force decoration above content. If a decorative element overlaps a content rectangle, move it, crop it, fade it, or remove it.

## Optional Inline Editing

Do not include inline editing by default in v1 unless the user asks. If included, keep controls outside the slide stage.
