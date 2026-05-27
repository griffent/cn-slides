# CN Slides

`cn-slides` is a Codex skill for creating Chinese business-style HTML slide decks.

`cn-slides` 是一个用于生成中文商务风格 HTML 演示文稿的 Codex Skill。

It focuses on clean Chinese typography, strong visual hierarchy, high-contrast business presentation styles, fixed 16:9 browser slides, and layout safety rules that prevent decorative elements from covering real content.

它重点解决中文排版、强视觉层级、高对比商务风格、固定 16:9 浏览器演示，以及装饰元素遮挡真实内容等问题。

## What It Creates / 可以生成什么

The skill is designed for Chinese slide decks such as:

这个 Skill 适合生成以下类型的中文 slides：

- company introductions / 公司介绍
- recruiting decks / 招聘资料
- project reviews / 项目复盘
- strategy reports / 战略汇报
- KPI and data reports / KPI 与数据报告
- product case studies / 产品案例
- internal sharing decks / 内部分享

The default output is a single self-contained HTML file with inline CSS and JavaScript. Slides are authored on a fixed `1920x1080` stage and scaled uniformly in the browser.

默认产物是一个单文件 HTML，CSS 和 JavaScript 都内联在文件中。每页按固定 `1920x1080` 舞台创作，并在浏览器中整体缩放。

## Included Styles / 内置风格

The skill includes five business presentation presets:

Skill 内置 5 套商务演示风格：

- `Clean Recruitment Blue` - white background, deep blue accents, dot matrix texture  
  白底、深蓝强调、点阵纹理，适合招聘资料、公司介绍、产品介绍。
- `Monochrome Corporate` - black/white/gray, strong numbering, consulting-style grids  
  黑白灰、强编号、咨询式网格，适合制度说明、组织结构、流程文档。
- `Bold Figure Report` - large numbers, minimal charts, data-first layouts  
  大数字、极简图表、数据优先，适合业务复盘、KPI 汇报、增长分析。
- `Geometric Culture Deck` - bright geometric blocks, warm culture/recruiting tone  
  明亮几何色块、温暖但克制，适合文化、团队、招聘、价值观内容。
- `Dark Contrast Studio` - black canvas, high-impact blue/purple type, keynote feel  
  黑底、高冲击蓝紫文字、超大编号，适合产品演讲、设计分享、技术主题。

## Installation For Codex / Codex 安装方式

Clone or download this repository, then copy the `cn-slides` folder into your Codex skills directory:

克隆或下载这个仓库，然后把 `cn-slides` 文件夹复制到 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
cp -R cn-slides ~/.codex/skills/cn-slides
```

After installation, invoke the skill in Codex with:

安装后，可以在 Codex 中这样调用：

```text
Use $cn-slides to create a clean, high-contrast Chinese business HTML slide deck from my notes.
```

中文也可以直接这样说：

```text
使用 $cn-slides，把我的笔记做成一份简洁、高对比的中文商务 HTML slides。
```

Or simply ask for a Chinese business slide deck in a context where Codex can discover installed skills.

如果 Codex 能发现已安装的 skills，也可以直接提出“做一份中文商务 slides”的需求。

## Repository Structure / 目录结构

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

## Design Principles / 设计原则

- Chinese-first typography and reading rhythm  
  中文优先的排版与阅读节奏
- clean layouts with strong contrast  
  简洁布局，但保持强烈主次对比
- fixed 16:9 stage behavior  
  固定 16:9 舞台，浏览器中整体缩放
- visual previews before full deck generation  
  先生成视觉方向预览，再扩展完整 deck
- restrained decoration  
  克制使用装饰元素
- explicit layout safety rules  
  明确的分层、间距和遮挡规则
- screenshot-oriented QA  
  以截图检查作为最终质量验证方式

The skill intentionally avoids generic AI template patterns such as purple gradients, glassmorphism, excessive card grids, random decorative shapes, and low-contrast text.

这个 Skill 会刻意避免常见的泛 AI 模板感，例如紫色渐变、玻璃拟态、过度卡片堆叠、随机装饰图形和低对比文字。

## Layout Safety / 布局安全

The skill includes a dedicated `layout-safety.md` reference.

Skill 内置了专门的 `layout-safety.md`，用来约束装饰元素、内容区域和页脚区域之间的关系。

Generated decks should separate every slide into:

生成 deck 时，每一页都应该按三层模型组织：

- `bg-layer` for background decoration  
  `bg-layer`：背景装饰层
- `content-layer` for actual slide content  
  `content-layer`：真实内容层
- `chrome-layer` for page numbers and deck UI  
  `chrome-layer`：页码、页脚和演示 UI 层

Decorative elements such as dot fields, giant letters, geometric blocks, quote marks, and chart textures must not cover text, UI mockups, charts, cards, footer labels, or page numbers.

点阵、超大字母、几何色块、引号、图表纹理等装饰元素，不能遮挡正文、UI mockup、图表、卡片、页脚标签或页码。

## Compatibility / 兼容性

This repository is a Codex skill source package.

这个仓库是 Codex Skill 源码包。

- Codex-compatible environments can install and invoke it as a skill.  
  支持 Codex Skills 的环境可以安装并通过 `$cn-slides` 调用。
- Other AI agents can read the skill files as design and workflow instructions.  
  其他 AI Agent 可以把这些文件作为设计规范和工作流说明来读取。
- Generic chat interfaces do not automatically install or invoke this skill, but you can paste `SKILL.md` and relevant reference files into context.  
  普通聊天型 AI 不会自动安装或调用这个 Skill，但可以把 `SKILL.md` 和相关 references 粘贴给它参考。
- Tools with different plugin/skill formats may require adaptation.  
  如果目标工具使用不同的插件或 Skill 格式，可能需要做目录结构或元数据适配。

## Notes / 注意事项

This skill does not currently handle PPT/PDF import, PDF export, or online deployment. It focuses on generating and improving browser-based HTML presentations.

当前版本不处理 PPT/PDF 导入、PDF 导出或在线部署，主要聚焦于生成和优化基于浏览器的 HTML 演示文稿。

