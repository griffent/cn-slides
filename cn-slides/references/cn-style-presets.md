# Chinese Business Style Presets

Use these as design systems, not rigid templates. Do not copy the user's reference PDFs; translate their shared visual language into original slides.

## Preset Selection

| Preset | Best For | Tone | Density |
| --- | --- | --- | --- |
| Clean Recruitment Blue | recruiting decks, company intros, culture decks | crisp, trustworthy, modern | medium to high |
| Monochrome Corporate | company profiles, org/process docs, policies | restrained, direct, consulting-like | high |
| Bold Figure Report | KPI reviews, business reports, growth updates | confident, analytical, executive | medium to high |
| Geometric Culture Deck | culture decks, onboarding, team narratives | warm, optimistic, editorial | low to medium |
| Dark Contrast Studio | keynote-style shares, product/design org decks | bold, digital, memorable | low to medium |

## Clean Recruitment Blue

**Vibe:** white corporate canvas, deep navy text, saturated blue emphasis, precise but energetic.

**Use when:** the deck is about recruiting, company overview, mission, values, organization, or product/business introductions.

**Typography:** heavy Chinese sans for titles, regular sans for body. Use bold weights for nouns and action verbs.

**Palette:**

```css
:root {
  --bg: #ffffff;
  --ink: #07182d;
  --muted: #5b6b7c;
  --blue: #0a66ff;
  --blue-dark: #003a8c;
  --line: #d9e2ee;
  --soft: #f4f8ff;
}
```

**Layout grammar:**

- Big Japanese/Chinese-style headline blocks, with key phrase reversed white-on-blue.
- Dot matrix fields or fine square grids in one corner, always behind content and outside the page-number safe zone.
- Small section label at top left and small page marker at bottom right.
- Body copy lives in a disciplined lower-left or lower-third block.

**Avoid:** bubbly cards, pastel softness, generic cloud shapes, dot fields covering section numbers or UI mockups.

## Monochrome Corporate

**Vibe:** black, white, and gray; direct; low decoration; strong numbering.

**Use when:** the deck needs to feel practical, credible, and easy to scan: company profiles, evaluation systems, org charts, process docs, internal explanations.

**Typography:** extra-bold numerals and section labels; medium body text.

**Palette:**

```css
:root {
  --bg: #f7f7f5;
  --ink: #161616;
  --muted: #666666;
  --light: #e6e6e2;
  --rule: #bdbdb7;
  --accent: #111111;
}
```

**Layout grammar:**

- Left-aligned content with large two-digit section numbers.
- Strict grids, tables, and simple line diagrams.
- Fine rule lines separate rows and columns; they must sit in gaps, not directly on top of card/mockup borders.
- Logo or deck label stays tiny in a corner.

**Avoid:** colorful backgrounds, decorative icons, soft shadows, duplicate rules that visually collide with content boxes.

## Bold Figure Report

**Vibe:** data first; huge black numbers; charts are supporting actors.

**Use when:** business review, fundraising, KPI recap, operating metrics, market size, performance report.

**Typography:** massive tabular numerals, heavy Chinese units, compact captions.

**Palette:**

```css
:root {
  --bg: #ffffff;
  --ink: #000000;
  --gray-900: #1f1f1f;
  --gray-600: #777777;
  --gray-300: #d8d8d8;
  --gray-100: #f2f2f2;
  --accent: #0a66ff;
}
```

**Layout grammar:**

- Key figures are 4-8x body text size.
- Charts use pale gray bars/lines with the current or important value in black/accent.
- Bottom metric strips work well: four columns, huge number plus short label.
- Notes are tiny and unobtrusive.

**Avoid:** colorful chart rainbows, unnecessary legends, 3D charts, decorative charts floating above UI mockups or body content.

## Geometric Culture Deck

**Vibe:** bright white space with large cropped geometric color blocks.

**Use when:** culture, hiring, people, values, onboarding, company story.

**Typography:** friendly bold sans; titles can be big and centered for section pages.

**Palette:**

```css
:root {
  --bg: #ffffff;
  --ink: #111111;
  --muted: #6f6f6f;
  --orange: #ff3b0a;
  --blue: #6388e8;
  --yellow: #f4e900;
  --green: #95bb3d;
  --brown: #6c2a20;
}
```

**Layout grammar:**

- Large polygons, circles, or cropped blocks sit at page edges as background framing.
- Center titles with a small section number above.
- Decorative brackets, double quotes, or parentheses can frame key words only when they are close enough to read as punctuation.
- Keep body pages lighter than section pages.

**Avoid:** confetti, cartoon illustrations, too many colors on one content-heavy page, detached quote marks, or shapes covering body cards/mockups.

## Dark Contrast Studio

**Vibe:** black canvas, electric blue/purple type, mint oversized page numbers.

**Use when:** design, product, technology, strategy, launch-style narratives, speaker-led decks.

**Typography:** very large bold sans; compressed section titles; small supporting Japanese/Chinese text.

**Palette:**

```css
:root {
  --bg: #050505;
  --ink: #f4f7ff;
  --blue: #5147ff;
  --purple: #6b5cff;
  --mint: #43e6a1;
  --coral: #ff6a4a;
  --muted: #8d8d99;
}
```

**Layout grammar:**

- Split black and saturated color panels.
- Oversized page numbers cropped at the lower right only when the lower-right area is otherwise empty.
- Big chapter titles with tiny bilingual captions.
- Use one vivid accent per slide; let black carry the drama.

**Avoid:** neon glow everywhere, cyberpunk clutter, low-contrast purple-on-black body text, giant letters covering footer labels, counters, UI mockups, or body text.

## Preview Mix Guidance

For conservative business users, preview:

- Monochrome Corporate
- Clean Recruitment Blue
- Bold Figure Report

For recruiting or culture decks, preview:

- Clean Recruitment Blue
- Geometric Culture Deck
- Monochrome Corporate

For product/design/keynote-style decks, preview:

- Dark Contrast Studio
- Clean Recruitment Blue
- Bold Figure Report
