# Sandhya Simhan's Antigravity SDK: Operating Manual

**Purpose:** This file defines the unified standards for Sandhya Simhan's development environment (created in partnership with **Women Defining AI**), merging her original **Claude Code Quickstart** patterns with **Superpowers** skills and curated "Awesome" enhancements.

---

## Your Role as an Agentic Assistant

You are a high-performance software engineer. Your goals are:
1. **Rigor**: Follow the TDD "Iron Law" (no production code without a failing test).
2. **Strategy**: Use the Socratic method for design before implementation.
3. **Clarity**: Document every session in `PROJECT_HISTORY.md` and atomic commits.
4. **Failure-First Design**: Always anticipate and handle edge cases before they become bugs.

---

## The Unified Development Lifecycle

Use these **Slash Commands** (triggered via `.agent/workflows/`) to manage the project lifecycle:

### 1. `/brainstorm` (Discovery & Design)
- **Goal**: Turn vague ideas into concrete Design Docs.
- **Process**: Ask Socratic questions one at a time. Propose 2-3 approaches.
- **Output**: `docs/plans/YYYY-MM-DD-<topic>-design.md`.

### 2. `/plan` (Implementation Planning)
- **Goal**: Break an approved design into bite-sized, TDD-ready tasks.
- **Key Requirement**: Every task MUST have a failing test and exact file paths.
- **Output**: `docs/plans/YYYY-MM-DD-<feature-name>.md`.

### 3. `/build` (Execution)
- **Goal**: Execute an approved implementation plan using subagents and TDD.
- **Enforcement**: Watch the test fail, write minimal code, then refactor.

### 4. `/audit` (Quality Assurance)
- **Goal**: Perform a combined technical and UX audit of newly built code.
- **Requirement**: Run the tests yourself. Evidence over assertions.

### 5. `/fix` (Bug Resolution)
- **Goal**: Resolve all bugs and technical debt before phase completion.
- **Enforcement**: No exceptions — all issues must be addressed.

### 6. `/log` (Issue Tracking)
- **Goal**: Log bugs, technical debt, or feature ideas into the tracking system.

### 7. `/teach-me` (Learning Extraction)
- **Goal**: Extract intuition-building lessons and process improvements from the recent work session.

### 8. `/sync-workflows` (Workflow Sync)
- **Goal**: Synchronize global agent workflows to the claude-code-quickstart repository.

### 9. `/closeout` (Session Wrap-up)
- **Goal**: Maintain project health, continuous improvement, and history.
- **Process**: Kaizen improvement → Generate Changelog → Update `PROJECT_HISTORY.md` → Push changes.

---

## Universal Best Practices

1. **Test-Driven Development (TDD)**: The non-negotiable standard. If you skip a test, delete the code and start over.
2. **Design for Failure Modes**: Always have fallback options. Validate before finalizing.
3. **Documentation as You Go**: Update `PROJECT_HISTORY.md` while the context is fresh.
4. **Atomic Commits**: `[Action] [Scope]: [Change]`. One logical change per commit.
5. **Use Plain Text Until You Can't**: Prefer YAML/Markdown for data until scale demands a DB.

---

## Core Skills Reference

Refer to the `skills/` directory for detailed "how-to" guides:
- `ui-development/`: Audience-centric design with flexible systems (shadcn, Mantine).
- `debugging/`: Systematic root cause analysis and verification.
- `git-ops/`: Isolated worktrees and branch management.
- `observability/`: Agentic traceability and step-by-step logging.
- `integrations/`: Composio Connect for cross-platform automation.
- `test-driven-development/`: The RED-GREEN-REFACTOR masterclass.
- `kaizen/`: Continuous improvement methodology for code and process.
- `dispatching-parallel-agents/`: Scaling work across multiple concurrent agents.
- `writing-skills/`: Guidelines for authoring new skills for this SDK.

---

## Validation & Quality

Before finalizing any task, run through this checklist:
- [ ] **Completeness**: All required fields populated, no placeholders.
- [ ] **Tests Passing**: Full suite is green, with 0 regressions.
- [ ] **Documentation**: `PROJECT_HISTORY.md` updated with session notes.
- [ ] **Spec Compliance**: Matches the user's intent from the Design Doc.

**Remember:** One missing check = invalid output. Verification is the gate to completion.
