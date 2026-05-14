# CV — auto-built workflow

**Source of truth:** `cv.tex` (XeLaTeX)
**Output:** `cv.pdf` (auto-generated, do not edit by hand)

## How to update the CV

1. Edit `cv.tex` locally (or directly on GitHub web editor).
2. Commit and push.
3. GitHub Actions runs `xelatex` and commits the new `cv.pdf` back to the repo (~1 min).
4. Homepage `Download CV` button is already linked to `cv/cv.pdf` — refreshes automatically.

## Why this setup

- LaTeX is the academic standard; diffs are readable and reviewable
- Single source of truth — no more "is the Word file or the PDF the latest?"
- GitHub Actions runs `xu-cheng/latex-action@v3` with full TeX Live + Noto CJK fonts, so the Chinese name (张天乐) renders correctly without any local setup
- Triggered only on changes to `cv.tex` or the workflow file → no infinite loops

## Local preview (optional)

```bash
# requires XeLaTeX + Noto Serif CJK SC
cd cv/
latexmk -xelatex cv.tex
```

## Conventions

- `\me{Tianle Zhang}` — bolds the name in author lists
- `\eq` — equal-contribution marker (`*`)
- `\corr` — corresponding-author marker (`†`)
- Section heads use `\section*{...}` (no numbering)

## To add a new publication

Copy the `\publication{...}{...}{...}{...}` block, change the 4 arguments:
1. venue tag (e.g., `NeurIPS'26`)
2. paper title
3. authors line (use `\me{Tianle Zhang}`, `\eq`, `\corr` as needed)
4. full venue line
