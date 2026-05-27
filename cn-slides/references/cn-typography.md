# Chinese Typography Rules

Design for Chinese first. English and numbers are supporting elements unless the user explicitly wants an English-first deck.

## Font Stack

Use system fonts by default:

```css
:root {
  --font-cn: "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei",
    "Noto Sans CJK SC", "Source Han Sans SC", sans-serif;
  --font-num: "DIN Alternate", "Arial Black", "Helvetica Neue", var(--font-cn);
}
```

Do not load remote fonts unless the user asks. Do not bundle font files in v1.

## Scale

At a `1920x1080` design size:

| Role | Suggested Size | Notes |
| --- | ---: | --- |
| Cover title | `104-176px` | short, bold, often 1-2 lines |
| Section title | `88-152px` | can pair with huge chapter number |
| Slide title | `54-88px` | keep one line when possible |
| Body | `28-42px` | high-density slides stay readable |
| Table text | `22-32px` | avoid smaller unless labels only |
| Caption/note | `16-22px` | only for source notes and footers |
| Key number | `140-260px` | 4-8x body size |

Keep at least three visible levels on most pages: title, body, caption or label.

## Chinese Line Length

- Cover and section titles: prefer `8-18` Chinese characters.
- Content slide titles: prefer `10-24` Chinese characters.
- Body lines: aim for `18-28` Chinese characters per line.
- Paragraphs: prefer `1-3` lines. Split longer text into bullets, callouts, or multiple slides.

## Line Height And Spacing

- Large Chinese titles: `line-height: 1.05-1.16`.
- Body Chinese text: `line-height: 1.45-1.7`.
- Bullets: use generous row gaps; do not pack bullets like a document.
- Tables: increase row height before reducing font size.

## Mixed Chinese, English, And Numbers

- Keep product names and proper nouns in their original form.
- Add visual breathing room around English fragments through layout, not random spaces.
- Use tabular numerals for KPI pages if available.
- Units such as `亿元`, `万人`, `%`, `倍` should be visually attached to numbers, but smaller than the number.
- Do not use full-width Latin letters for English words.

## Headlines

Prefer concrete short statements:

- Good: `增长进入第二曲线`
- Good: `组织能力需要提前建设`
- Weak: `关于我们的一些情况介绍`

For impact pages, highlight one phrase using color block reversal, oversized type, or a separate line.

## Text Density

Low-density pages:

- 1 idea
- 1 title
- 0-3 supporting bullets
- one strong visual device

High-density pages:

- 1 title
- 2-4 structured regions
- tables, matrices, timelines, or annotated metrics
- no scrolling and no tiny body text

## Punctuation And Copy

- Use Chinese punctuation in Chinese sentences.
- Avoid long comma chains. Break complex points into multiple lines or numbered rows.
- Avoid decorative emoji in business decks.
- Use concise labels: `现状`, `问题`, `策略`, `下一步`, `指标`, `影响`.

