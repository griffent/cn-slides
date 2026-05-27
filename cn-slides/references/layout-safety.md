# Layout Safety Rules

Use these rules to prevent the common failure mode where decorative elements look stylish in isolation but cover the actual slide content.

## Layer Model

Every slide should use three conceptual layers:

```html
<article class="slide">
  <div class="bg-layer" aria-hidden="true"></div>
  <div class="content-layer">...</div>
  <div class="chrome-layer">...</div>
</article>
```

```css
.slide { position: absolute; isolation: isolate; }
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
```

Decorative elements default to `.bg-layer`. Content, charts, UI mockups, tables, and cards default to `.content-layer`. Page numbers, deck labels, and progress indicators belong to `.chrome-layer`.

## Foreground Decoration Rule

Do not place decorative items above real content. This includes:

- dot fields
- geometric blocks
- quote marks
- oversized page numbers
- oversized letters such as `FG`
- charts used only as visual texture
- fine grid lines or rules

Foreground decoration is allowed only when it is the primary message of the slide, not when it competes with body content. If a decorative element touches or crosses a content box, either move it behind the content, crop it to a margin, reduce opacity below `0.12`, or remove it.

## Safe Zones

Reserve these areas on every `1920x1080` slide:

- outer slide margin: at least `96px`
- footer zone: bottom `120px`, reserved for style label, page number, and quiet whitespace
- page number zone: right `220px` x bottom `120px`
- title-to-content gap: at least `56px`
- two-column gap: at least `56px`
- card/grid gap: at least `28px`
- UI mockup internal edge padding: at least `36px`

No chart, big letter, circle, color block, or illustration may enter the footer or page number zone unless it is extremely faint background texture and does not reduce readability.

## Content Box Rules

Treat each semantic region as a solid rectangle and keep it clean:

- A text block, card, metric, table, chart, or UI mockup must not overlap another semantic region.
- A chart should never float on top of a UI mockup unless the mockup is intentionally a faded backdrop with opacity below `0.15`.
- A fine rule or divider must sit in its own gap, not exactly on the border of a nearby card or mockup.
- Decorative shapes can be cropped by slide edges, but not by content boxes.
- If a page has both a mockup and a statement panel, use a clear grid: two columns, one content block per column.

## Preset-Specific Safety

### Clean Recruitment Blue

- Dot matrices belong in a corner background. Keep them behind text and away from the page number.
- If the slide has a large section number, do not place dot matrix behind the number unless contrast remains high.
- Blue reversed title blocks are content, not decoration; they must not collide with other text.

### Monochrome Corporate

- Rules and divider lines must live between regions. Do not align a rule exactly on top of a mockup/card border.
- Use tables and grids as content, not background texture.
- Keep at least `32px` between a mockup edge and any external rule.

### Bold Figure Report

- Charts are content. Do not overlay charts on UI mockups or body cards.
- If a chart is decorative context, make it a faint background texture below `0.12` opacity.
- Big numbers should dominate their own region, not sit on top of labels or charts.

### Geometric Culture Deck

- Large color shapes should be edge-cropped backgrounds. They may frame content but must not cover words, cards, mockups, or footer labels.
- Quote marks should frame a title only when close enough to be read as punctuation. Do not leave detached quote marks far from the text.
- Avoid placing multiple saturated shapes around content-heavy pages.

### Dark Contrast Studio

- Oversized letters and page numbers belong behind content or in a reserved empty corner.
- If a large `FG`/page number overlaps UI mockups, footer labels, or page counters, move it behind the mockup with low opacity or crop it farther outside the canvas.
- Keep body text contrast high; purple-on-black is only for large titles.

## Layout Decision Order

When space is tight, make decisions in this order:

1. Preserve content readability.
2. Preserve clear semantic grouping.
3. Preserve navigation and page markers.
4. Keep one strong decorative device.
5. Remove secondary decoration.

Do not shrink text or overlap regions just to preserve decorative style.

