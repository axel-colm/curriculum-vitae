# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build

```bash
cd cv
latexmk -pdf -xelatex main.tex   # preferred: XeLaTeX for font support
# or
pdflatex main.tex                 # fallback (fonts may differ)
```

Output: `cv/main.pdf`

Clean build artifacts:
```bash
cd cv && latexmk -C
```

## Structure

LaTeX CV built on [AltaCV](https://github.com/liantze/AltaCV) v1.7.3 (`altacv.cls`).

- `cv/main.tex` — entry point: colors, layout, column ratios, section order via `\input{}`
- `cv/experience/` — one `.tex` per job (`\cvevent` + bullet list + `\cvsmalltag`)
- `cv/project/` — one `.tex` per project (same pattern)
- `cv/skills.tex` — skills tags and language section
- `cv/education.tex` — education section
- `cv/images/profile.jpg` — headshot

## Layout

Two-page layout:
- **Page 1, left col (58%)**: Experience
- **Page 1, right col (42%)**: Skills, Education
- **Page 2**: Projects grid (single `paracol` block)

Column ratio set at `\columnratio{0.58}` (page 1) and `\columnratio{0.5}` (page 2).

## AltaCV macros

Key macros used throughout:

| Macro | Purpose |
|---|---|
| `\cvevent{Title}{Org}{Dates}{Location}` | Job/project header |
| `\cvsmalltag{text}` | Inline tech tag (experience) |
| `\cvtag{text}` | Larger tag (skills) |
| `\cvskill{name}{rating}` | Skill with dot rating (0–5) |
| `\divider` | Horizontal rule between entries |

## Colors

Theme uses dark-red headings (`DarkPastelRed #450808`) with green accents (`LightPastelGreen #8FBF8D`). Colors defined at top of `main.tex`.
