# CN Slides

`cn-slides` is a Codex skill for creating Chinese business-style HTML slide decks.

It focuses on clean Chinese typography, strong visual hierarchy, high-contrast business presentation styles, fixed 16:9 browser slides, and layout safety rules that prevent decorative elements from covering real content.

## What It Creates

The skill is designed for Chinese slide decks such as:

- company introductions
- recruiting decks
- project reviews
- strategy reports
- KPI and data reports
- product case studies
- internal sharing decks

The default output is a single self-contained HTML file with inline CSS and JavaScript. Slides are authored on a fixed `1920x1080` stage and scaled uniformly in the browser.

## Included Styles

The skill includes five business presentation presets:

- `Clean Recruitment Blue` - white background, deep blue accents, dot matrix texture
- `Monochrome Corporate` - black/white/gray, strong numbering, consulting-style grids
- `Bold Figure Report` - large numbers, minimal charts, data-first layouts
- `Geometric Culture Deck` - bright geometric blocks, warm culture/recruiting tone
- `Dark Contrast Studio` - black canvas, high-impact blue/purple type, keynote feel

## Installation For Codex

Clone or download this repository, then copy the `cn-slides` folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R cn-slides ~/.codex/skills/cn-slides
```

After installation, invoke the skill in Codex with:

```text
Use $cn-slides to create a clean, high-contrast Chinese business HTML slide deck from my notes.
```

Or simply ask for a Chinese business slide deck in a context where Codex can discover installed skills.

## Repository Structure

```text
cn-slides/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── cn-style-presets.md
    ├── cn-typography.md
    ├── html-template.md
    ├── layout-safety.md
    └── verification.md
```

## Design Principles

- Chinese-first typography and reading rhythm
- clean layouts with strong contrast
- fixed 16:9 stage behavior
- visual previews before full deck generation
- restrained decoration
- explicit layout safety rules
- screenshot-oriented QA

The skill intentionally avoids generic AI template patterns such as purple gradients, glassmorphism, excessive card grids, random decorative shapes, and low-contrast text.

## Layout Safety

The skill includes a dedicated `layout-safety.md` reference.

Generated decks should separate every slide into:

- `bg-layer` for background decoration
- `content-layer` for actual slide content
- `chrome-layer` for page numbers and deck UI

Decorative elements such as dot fields, giant letters, geometric blocks, quote marks, and chart textures must not cover text, UI mockups, charts, cards, footer labels, or page numbers.

## Compatibility

This repository is a Codex skill source package.

- Codex-compatible environments can install and invoke it as a skill.
- Other AI agents can read the skill files as design and workflow instructions.
- Generic chat interfaces do not automatically install or invoke this skill, but you can paste `SKILL.md` and relevant reference files into context.
- Tools with different plugin/skill formats may require adaptation.

## Notes

This skill does not currently handle PPT/PDF import, PDF export, or online deployment. It focuses on generating and improving browser-based HTML presentations.

