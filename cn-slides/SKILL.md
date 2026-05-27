---
name: cn-slides
description: Create or improve Chinese business-style HTML slide decks with clean high-contrast visual systems, strong Chinese typography, fixed 16:9 browser presentation behavior, and visual style discovery. Use when the user wants Chinese slides, a Chinese business deck, company introduction, recruiting deck, project review, strategy report, data report, or Japanese/Chinese corporate deck-inspired web presentation.
---

# CN Slides

Create Chinese business-style, single-file HTML presentations. The default output is a self-contained `.html` deck with inline CSS and JavaScript, authored on a fixed `1920x1080` stage and scaled as one unit in the browser.

## Core Principles

1. **Chinese-first business design** - Design around Chinese typography, Chinese reading rhythm, and corporate reporting contexts.
2. **Clean plus contrast** - Keep backgrounds simple, then create impact through large type, strong numbering, bold color blocks, and data hierarchy.
3. **Show, don't tell** - Generate visual previews before the final deck unless the user explicitly names a preset.
4. **Fixed 16:9 stage** - Slides are authored at `1920x1080`; the stage scales uniformly to the viewport. Do not reflow slide content for phones.
5. **No generic AI templates** - Avoid purple gradients on white, glassmorphism, decorative card grids, and vague startup-style visuals.

## Mode Detection

- **New deck** - Create a new Chinese business presentation from a topic, notes, outline, or source material.
- **Enhance HTML deck** - Improve an existing HTML presentation while preserving fixed-stage behavior.

This skill does not convert PPT/PDF files, export PDF, or deploy online in v1. If the user asks for those, say they are outside this skill and use another available workflow if appropriate.

## Discovery

For new decks, ask all missing essentials together:

- Purpose: project review, company introduction, recruiting deck, strategy report, data report, training/share-out, other.
- Length: short `5-10`, medium `10-20`, long `20+`.
- Content state: all content ready, rough notes, topic only.
- Density: low-density speaker-led, or high-density reading-first.
- Brand constraints: optional colors, logo/images, required terms, forbidden styles.

If the user already gave enough information, proceed with reasonable defaults. For Chinese business decks, default to medium length and high-density reading-first unless the deck is clearly for a live speech or launch-style presentation.

## Style Discovery

Read `references/cn-style-presets.md` before choosing styles.

Generate three distinct single-slide HTML previews by default:

- one safe corporate option
- one high-contrast option
- one expressive but still business-appropriate option

Previews must look like real first slides or section slides from the user's deck. Do not render internal labels such as "preview", "preset", "option A", file names, workflow notes, or template names inside the slide itself. Style names belong only in the chat message.

After previews, ask the user which direction to use. If they want to mix elements, capture the mix as the final design recipe.

## Final Generation

Before generating the final deck, read:

- `references/cn-typography.md` for Chinese layout and text rules
- `references/html-template.md` for fixed-stage HTML structure and controls
- `references/layout-safety.md` for layering, spacing, and collision rules
- `references/verification.md` for the final QA checklist

Use the chosen preview or preset as the design recipe. Preserve its typography, palette, spacing, decorative vocabulary, and page rhythm across title, section, content, data, comparison, timeline, quote, and closing slides.

### Density Rules

- **Low-density speaker-led** - One idea per slide, huge titles, short phrases, strong section beats, more slides.
- **High-density reading-first** - Self-contained slides with clear grids, tables, matrices, annotated numbers, and concise explanatory text.

If content exceeds the chosen density, split into more slides rather than shrinking text until it becomes cramped.

## Non-Negotiable Output Rules

- Single self-contained HTML file with inline CSS and JavaScript.
- Every slide is `1920px x 1080px` inside one scalable stage.
- No slide-level scrolling.
- No responsive re-layout inside slides.
- No overlapping text, clipped cards, or unreadably small text.
- No decorative element may cover body text, page numbers, UI mockups, charts, or cards.
- Keyboard navigation must work with arrow keys, space, page up/down, home/end.
- Touch or swipe navigation should work on mobile.
- Include `prefers-reduced-motion` support.
- Use system Chinese fonts first; do not load remote fonts unless the user explicitly asks.

## Visual Guardrails

Use:

- large title contrast
- oversized section numbers or page numbers
- high-saturation accent colors on neutral backgrounds
- restrained geometric blocks, dot matrices, fine rules, brackets, or quote marks
- data-first layouts where key figures dominate the page
- clean tables, timelines, matrices, and split layouts

Avoid:

- generic purple-blue gradients
- rounded card grids as the default layout
- ornamental illustrations unrelated to content
- foreground decoration that floats over real content
- detached quote marks, giant letters, page numbers, charts, or shapes whose only role is decoration
- small dense paragraphs
- excessive shadows, blur, glass effects, or emoji
- copying logos, page content, or proprietary graphics from visual references unless the user owns and provides them for use

## Modification Rules

When improving an existing HTML deck:

1. Inspect its stage model and slide switching first.
2. Preserve or convert to fixed `1920x1080` stage behavior.
3. Apply Chinese typography and contrast improvements without changing the user's message.
4. Remove or demote decorative elements that overlap content; decoration belongs behind content unless it is the main message.
5. After edits, verify the deck at desktop and phone viewports.
