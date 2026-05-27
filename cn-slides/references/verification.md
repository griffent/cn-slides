# Verification Checklist

Run these checks before handing off a generated or modified deck.

## Visual Fit

- The stage remains exactly `1920x1080`.
- The browser scales the whole stage; slide content does not reflow at phone width.
- No slide has scrollbars.
- No text is clipped by its container.
- No panels, chart labels, tables, or decorative shapes overlap incoherently.
- No decorative element sits above or covers content, UI mockups, chart labels, footer labels, or page numbers.
- Footer labels and page numbers have a clear safe zone and are never covered by oversized letters or shapes.
- Divider lines sit in gaps between regions; they do not coincide with card or mockup borders.
- Captions and footnotes are readable, even if intentionally small.

## Chinese Readability

- Titles are short and strong.
- Body lines are not document-length paragraphs.
- Chinese line height feels comfortable.
- Mixed English/numbers do not create awkward spacing.
- Key numbers dominate data pages.

## Style Integrity

- The final deck follows the selected preview or preset consistently.
- Accent colors are limited and purposeful.
- Decorative elements are restrained and correctly layered: dot matrix, grids, geometric blocks, large numbers, rules, brackets.
- Dot matrices, quote marks, giant letters, and geometric shapes read as background or framing, not as accidental foreground clutter.
- The deck does not look like a generic AI-generated template.
- No copied brand graphics or proprietary page content from visual references unless explicitly provided for reuse.

## Interaction

- Arrow keys navigate correctly.
- Space and page up/down navigate correctly.
- Home/end jump to first/last slide.
- Touch swipe works on mobile.
- Progress and counter match the current slide.
- `prefers-reduced-motion` is supported.

## Screenshot Review

When a browser tool is available, inspect screenshots at:

- desktop: `1280x720` or larger
- phone: a narrow viewport such as `390x844`

Screenshot checks matter because DOM scroll metrics alone may miss visual overlap.

## Collision Review

For every generated deck, manually inspect at least:

- one cover slide
- one normal content slide
- one data/chart slide
- one dark or highly decorative slide
- one closing slide

If any screenshot needs a red-arrow explanation like "this should be background", the slide fails QA. Fix by changing the layer model or removing the decoration, not by explaining it away.
