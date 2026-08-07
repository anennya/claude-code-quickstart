# Build Together Deck Style Guide

Extracted from `claude_skills_build_together_2.pptx` (17 slides) by measuring the actual XML — colors,
fonts, sizes, and positions below are what the deck uses, not a guess. Use this as the default visual
system for any deck, slide, or report unless the user explicitly asks for something different.

## Canvas

- 16:9 widescreen, 13.33in × 7.5in (12,191,695 × 6,858,000 EMU).
- Content margin: **0.85in** left and right on every content slide (content width 11.63in).
- Header row (kicker/eyebrow) starts at **y = 0.5in**, height 0.3in.
- Footer page number sits bottom-right: box at x=10.48in, y=7.10in, w=2.0in, h=0.4in, right/center
  aligned, format `"N / total"`.
- No bullet characters anywhere in the deck (`buNone` throughout) — body copy runs as flowing
  paragraphs or lives inside labeled cards, never a bulleted list.
- Paragraph line spacing: 115% typical; loosen to 130% for short, airy body paragraphs.

## Color Palette

| Hex | Role | Usage |
|---|---|---|
| `#FAF7F5` | Background | Slide background on every single slide (warm off-white/cream, not pure white) |
| `#211D33` | Primary ink | Headlines, titles, primary body text — near-black deep indigo, never pure `#000000` |
| `#595465` | Secondary text | Body copy, supporting paragraphs, descriptions |
| `#9A97A5` | Tertiary text | Page numbers, meta labels, low-emphasis captions |
| `#D6437E` | Primary accent (brand pink) | Eyebrow/kicker labels, accent numerals, small emphasis words, icon-circle borders |
| `#815C9A` | Secondary accent (purple) | Card borders/outlines, dark-bold text on light pill badges |
| `#281F4F` | Deep accent | Bold label text on light pill badges (alternate to pink) |
| `#2B2B38` | Dark contrast panel | Solid-fill emphasis/CTA panels, paired with white bold text |
| `#EDEAF4` | Light lavender surface | Card and pill fills |
| `#FBEAF0` | Light pink surface | Card/pill fill variant, icon-circle fill |
| `#D9D5DD` | Neutral divider | Thin 1pt divider lines between sections |
| `#FFFFFF` | White | Text on dark panels/photos; rarely a background |
| `#D74881` | Bright pink accent | Full-width top accent bar on the title/cover slide only |

Never introduce a new brand color without asking — this palette (warm cream + indigo ink + pink/purple
duo) is the whole system. Do not substitute pure black or pure white for text/background.

## Typography

Two typefaces only:

- **Playfair Display** — serif, used exclusively for emphasis: big single-statement headlines and
  small numeral/label accents. Never used for body copy or UI chrome.
- **Inter** — sans, used for everything else: eyebrow labels, slide titles, body copy, buttons/pills,
  footers.

| Role | Font | Size | Weight/Style | Color | Notes |
|---|---|---|---|---|---|
| Hero statement (cover-style headline) | Playfair Display | 28–44pt | Bold | `#211D33` | One short sentence, own slide moment |
| Section headline | Playfair Display | 26–30pt | Bold | `#211D33` | Slide-level big statement |
| Accent numeral/label | Playfair Display | 12–14pt | Bold Italic | `#D6437E` (sometimes `#211D33`) | e.g. "No. 01", "0–5" — recurring numbering motif |
| Eyebrow / kicker | Inter | 10.5–12pt | Bold, uppercase, letter-spaced (+1pt / `spc="100"`) | `#D6437E` or `#281F4F` | Sits directly above a headline or section title |
| Slide title | Inter | 12–13pt | Bold | `#211D33` | Compact title bar text |
| Body copy | Inter | 11–14pt | Regular | `#595465` | Paragraph form, no bullets |
| Pill/button label | Inter | 11pt | Bold | `#FFFFFF` (on dark) or `#281F4F` (on light pill) | Centered in roundRect |
| Footer/meta | Inter | 10pt | Regular | `#9A97A5` | Page numbers, timestamps |

## Layout Components

- **Pills / badges**: `roundRect`, fully rounded corners (radius = 50% of shorter side), fill
  `#EDEAF4`, centered bold Inter label. Used for status tags like "LIVE · BUILD TOGETHER".
- **Cards**: `roundRect` with a small fixed corner radius (roughly 8–12px equivalent — computed as a
  percentage of the shape's own size, not a flat %). Fill `#EDEAF4` or `#FBEAF0`; optional 1pt border
  in `#815C9A`. Use for grouped content, feature call-outs, or step boxes.
  - Alternate "outline" card: fill matches background `#FAF7F5`, 1–1.25pt border `#815C9A` — reads as a
    ghost/outlined card on the cream background.
- **Dark panels**: plain `rect`, solid fill `#2B2B38`, paired with white bold Inter text — used for a
  single emphasis block or CTA-style panel per slide, sparingly.
- **Icon circles**: `ellipse`, fill `#FBEAF0`, border `#D6437E` (~1.5pt) — small decorative or avatar
  containers.
- **Dividers**: plain 1pt lines, color `#D9D5DD`, used to separate stacked sections within a slide.
- **Top accent bar**: full-width thin rect (0.09in tall), fill `#D74881` — cover/title slide only, not
  repeated on content slides.

## Recurring Motifs

1. **Kicker + headline pairing**: a short uppercase Inter eyebrow label directly above a large
   Playfair Display statement. This is the default way to open a slide's main idea.
2. **Numeral accents**: section or step numbers set in Playfair Display, bold italic, pink — treated as
   a design detail, not just a label (e.g. "No. 01", "0–5").
3. **No bullets, ever**: lists become short paragraphs, numbered accent labels, or a row of cards.
4. **One big single-line statement per hero moment**: don't crowd a headline slide with supporting
   text; let the Playfair Display line stand alone, with body detail on the slide below/after.
5. **Consistent footer**: every content slide gets a bottom-right "N / total" page counter in the same
   position and style.

## Applying this to a new deck/report

- Default background: `#FAF7F5`. Default text: `#211D33` (primary) / `#595465` (secondary).
- Reach for Playfair Display only for the one big statement per slide or a numeral accent; Inter for
  literally everything else.
- Keep the 0.85in side margins and bottom-right page counter on every slide.
- If asked for a report (not slides), carry the same palette and type pairing into the document:
  Playfair Display for section headers/pull-quotes, Inter for body, same color roles.
- If the request conflicts with this system (e.g. "make it dark mode" or "use our other brand
  colors"), ask before overriding — don't silently blend two systems.
