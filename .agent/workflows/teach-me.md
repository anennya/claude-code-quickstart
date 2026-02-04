---
description: Extract intuition-building lessons and process improvements from the recent work session.
---

# /teach-me Methodology

Use this workflow to maximize the "ROI" of a coding session by extracting lessons, simplifications, and workflow improvements.

## 1. Intuition Training (Symptom → Fix)
- [ ] **The "Tell"**: What was the specific visual glitch, error message, or behavior that betrayed the root cause? 
    - *Goal*: Build the user's "muscle memory" for diagnosing this specific issue next time.
- [ ] **The Shortcut**: What is the 30-second check to confirm this diagnosis before diving deep?

## 2. The Mental Model
- [ ] **Simplify**: Explain the most complex part of the recent logic using a non-technical analogy (e.g., "The Store is just a backpack that persists between pages").
- [ ] **The "Black Box"**: explicitly identify parts of the system the user can *safely ignore* to move faster.

## 3. The Simplicity Check (Code quality)
- [ ] **The "Delete" Button**: Look at the final code. Is there any part we *could* have skipped without hurting the user experience?
- [ ] **Complexity Audit**: Did we solve a simple problem with a complex tool? (e.g., "We used Redux but `useState` would have worked.")

## 4. Vibe Optimization (Process)
- [ ] **Friction Hunter**: Identify the exact moment the session felt "slow" or "stuck".
- [ ] **The Unblocker**: Suggest one workflow change (keybinding, command alias, or habit) to eliminate that friction next time.

## 5. Meta-Evolution (Workflow Updates)
- [ ] **The "Patch"**: Based on the learnings above, suggest specific text updates for *any* relevant workflow (`/brainstorm`, `/plan`, `/build`, `/code-review`, `/fix`, `/verify-ux`, `/closeout`) to prevent this issue recurring.
    - *Example*: "We forgot timeouts. Add 'Timeout Check' to `/code-review`."
- [ ] **The New Path**: If this learning reveals a completely missing process, suggest a *new* workflow file (e.g., `/debug-server`).
- [ ] **The Prompt**: Provide the exact markdown snippet to insert into the target workflow file.

## 6. Summary
- [ ] **One-Sentence Mantra**: A catchy takeaway rule for next session (e.g., "Always check the Network tab before checking the Database").
