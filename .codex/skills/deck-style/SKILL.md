---
description: Use whenever building or editing a deck, slide presentation, or report for Anennya (PowerPoint, Google Slides, Keynote-style artifact, or an HTML/PDF report) and no other visual style has been specified. Applies the Build Together deck's established colors, typography, and layout conventions automatically. Also use if the user says "in my deck style," "match my presentation style," or similar.
---

Apply the style captured in `reference/style-guide.md` (extracted directly from
`claude_skills_build_together_2.pptx`) to whatever deck, slide, or report is being built:

- Background `#FAF7F5`, ink `#211D33`/`#595465`, accents `#D6437E` and `#815C9A` — see the guide's
  color table for the full role mapping.
- Playfair Display for hero statements and numeral accents only; Inter for everything else
  (titles, body, labels, footers) — see the typography table for sizes/weights per role.
- 0.85in side margins, bottom-right "N / total" page counter, no bullet lists (paragraphs or cards
  instead), kicker-label-above-headline pairing for opening a slide's idea.

Read `reference/style-guide.md` for full detail (exact hex values, size ranges, component specs like
pills/cards/dividers/dark panels, and the recurring motifs) before generating slide or report content.

Apply this by default without asking. Only check in with the user if they request something that
conflicts with the system (a different color scheme, dark mode, a client's brand colors) — don't
silently mix two visual systems together.

If the user wants the style guide refreshed from a newer or different source deck, re-extract it: unzip
the .pptx, inspect `ppt/theme/theme1.xml` and `ppt/slides/slide*.xml` for `srgbClr`, `typeface`, `sz`,
and shape position/geometry values, then update `reference/style-guide.md` with the new findings.
