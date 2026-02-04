---
description: Perform an interactive UX audit and verify design consistency against BRAND_GUIDELINES.md.
---

# /verify-ux

Use this workflow when a feature is "code complete" but needs verification of the user experience and aesthetics.

## Core Principles
- **Interaction Over Code**: Focus on how the app feels.
- **Aesthetic Rigor**: Every pixel must align with `BRAND_GUIDELINES.md` (Teal `#0078AA` anchor, Playful Illustrated Minimalism).

## The Process

1. **Environment Check**
   - Run `npm run dev` to ensure the local dashboard is active.
   - Open [http://localhost:3000].

2. **Manual UX Triage (The Checklist)**
   - [ ] **Functional**: Does every button do what it says?
   - [ ] **Feedback**: Are there loading indicators / toasts? (Prefer **Skeleton Loaders** for perceived speed over full-screen spinners).
   - [ ] **Aesthetics**: Does it match the Teal/Mustard color world?
   - [ ] **Dark Mode Parity**: Verify visibility and theme variables in both Light and Dark modes.
   - [ ] **Distraction-Free Audit**: Does the focused view (e.g. Reader) remove unnecessary global navigation?
   - [ ] **Responsiveness**: Check mobile vs desktop layout.
   - [ ] **Brand**: Does it feel "Playful and Creative" as per guidelines?

3. **Discovery & Fixes**
   - Any UX polish items found should be added to `BUGS.md` immediately with the prefix `[UX]`.
   - Fix small spacing or color issues immediately.

**Next Step**: Once UX verification is passing:
1. Run **`/teach-me`** to extract lessons from this session.
2. Then run **`/closeout`** to finalize the phase.
