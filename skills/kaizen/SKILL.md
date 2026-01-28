---
name: kaizen
description: Use during /closeout or between development iterations to apply continuous improvement (Kaizen) analysis to the codebase and process.
---

# Kaizen: Continuous Improvement

## Overview
Based on Japanese Lean methodology, Kaizen is the practice of continuous, incremental improvement. This skill ensures that every session doesn't just "finish" but also makes the system better, cleaner, and more efficient.

## The Kaizen Loop

**USAGE**: Trigger this during `/closeout` to identify one small improvement to make before finalizing.

### Focus Areas
1. **The 3Ms of Waste**:
   - **Muda (Waste)**: Remove dead code, redundant comments, or unused dependencies.
   - **Mura (Inconsistency)**: Standardize naming conventions or UI styles across related files.
   - **Muri (Overburden)**: Simplify over-complex functions or logic that "smells."

2. **Process Refinement**:
   - Did a tool call fail repeatedly? Update the skill or project context to prevent it.
   - Was a manual step tedious? Automate it or create a workflow.

## Implementing Improvements
Small, atomic changes are better than a single massive refactor. 
- "Refactor `auth.ts` to use helper" is a better Kaizen than "Rewrite auth system."

## Verification Checklist
- [ ] Codebase is cleaner than it was at the start of the session.
- [ ] At least one instance of "Muda" (waste) identified and addressed.
- [ ] Process friction documented and mitigation proposed (or implemented).
- [ ] Improvements are atomic and TDD-verified.
