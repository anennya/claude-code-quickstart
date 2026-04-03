# Sandhya Simhan's Claude Code SDK: Unified Agentic Tooling

Building an app with Claude Code is powerful — but without structure, sessions drift, context gets lost, and it's hard to know what to do next.

This repo gives you a repeatable system for going from idea to working app. It provides an opinionated development lifecycle (brainstorm → plan → build → audit → fix → ship), enforces test-driven development, and keeps a running history of every session. Use it as a reusable SDK that sits on your machine and plugs into any project — or follow along as a workshop participant.

It's for anyone who wants to build with Claude Code and not start from scratch every time.

## Core Features

- **Standardized Workflows**: Consistent slash commands for `/brainstorm`, `/design`, `/implement`, `/connect`, and `/closeout`.
- **TDD-First Culture**: Built-in enforcement of Test-Driven Development as a non-negotiable standard.
- **Audience-Centric UI**: Flexible design systems (shadcn, Mantine) driven by deep audience research.
- **Agentic Traceability**: Structured observability and logging for complex multi-agent workflows.
- **Systematic Debugging**: Root cause analysis and verification principles.
- **Git Isolation**: Smart use of git worktrees to prevent workspace pollution.
- **Global Integrations**: Connect to 1000+ apps via Composio.
- **Persistent History**: Automated session tracking in `PROJECT_HISTORY.md` and automated changelogs.

## Getting Started

### Prerequisites

- **Claude Code installed** — Mac app or CLI
- **Verify slash commands work** by typing `/` in Claude Code and checking that commands appear in autocomplete
- If commands don't appear in the terminal, see [Troubleshooting](#troubleshooting) below

---

### How to Use This Repo

Clone this repo once and keep it on your machine. It acts as a shared toolkit — when you start a new app, you copy one file (`CLAUDE-template.md`) into your project and it pulls in all the commands, rules, and workflows from here automatically. You never need to copy the whole thing.

---

### One-Time Setup

**1. Clone the repo:**
```zsh
git clone https://github.com/anennya/claude-code-quickstart.git
cd claude-code-quickstart
```

**2. Fix the `@` import path** — run this from inside the repo directory so `CLAUDE-template.md` knows where the SDK lives on your machine:
```
sed -i '' "s|@/PATH/TO/claude-code-quickstart|@$(pwd)|g" CLAUDE-template.md
```
Verify it worked: `head -3 CLAUDE-template.md` should show your actual path, not `/PATH/TO/...`.

**3. Install slash commands** — this makes `/brainstorm`, `/plan`, `/build` etc. available in Claude Code:

*Globally (recommended) — available in every project:*
```zsh
mkdir -p ~/.claude/commands && cp .claude/commands/*.md ~/.claude/commands/
```

*Per-project — copy into a specific project instead:*
```zsh
cp -r /path/to/claude-code-quickstart/.claude ~/your-new-project/
```
Restart Claude Code after either option.

**4. Install skills** — skills enhance the commands with deeper guidance (TDD, UI design, architecture, etc.). They're not required for commands to work, but recommended.

*Globally (recommended) — available in every project:*
```zsh
mkdir -p ~/.claude/skills && cp -r skills/* ~/.claude/skills/
```

*Per-project — copy into a specific project instead:*
```zsh
cp -r /path/to/claude-code-quickstart/skills ~/your-new-project/
```

---

### Starting a New Project

1. Create your new project folder and initialize git
2. Copy `CLAUDE-template.md` into it as `CLAUDE.md`:
   ```
   cp /path/to/claude-code-quickstart/CLAUDE-template.md ~/your-new-project/CLAUDE.md
   ```
3. Fill in the fields at the top of `CLAUDE.md` — name, purpose, stack, constraints
4. Open Claude Code in your project — it picks up `CLAUDE.md` automatically

> **Don't run `/init`** — that command reverse-engineers an existing codebase into a `CLAUDE.md`. You already have one; running `/init` would overwrite it.

---

### Your First Session

Open Claude Code in your project and type `/brainstorm`. Bring any rough idea — it doesn't need to be fully formed. Claude will ask Socratic questions one at a time to sharpen it, then produce a design doc in `docs/plans/`.

---

### The Development Lifecycle

Work through these commands in order for each feature:

| Command | When to use |
|---|---|
| `/brainstorm` | Turn a rough idea into a design doc |
| `/plan` | Break an approved design into TDD-ready tasks |
| `/build` | Execute the plan using subagents and TDD |
| `/audit` | Review finished code — runs tests, produces evidence |
| `/fix` | Resolve all bugs and debt flagged by the audit |
| `/log` | Log a bug or idea without starting work on it |
| `/teach-me` | Extract lessons from the session |
| `/closeout` | Changelog, update `PROJECT_HISTORY.md`, commit and push |

---

### Where Things Live

| What | Where |
|---|---|
| Design docs | `docs/plans/YYYY-MM-DD-<topic>-design.md` |
| Implementation plans | `docs/plans/YYYY-MM-DD-<feature-name>.md` |
| Session history | `PROJECT_HISTORY.md` |
| Slash commands | `.claude/commands/` (project) or `~/.claude/commands/` (global) |
| Skills reference | `skills/` |

---

### Where to Go From Here

- **Customize your `CLAUDE.md`**: Add project-specific rules and conventions as your app evolves
- **Write your own slash commands**: Add `.md` files to `.claude/commands/` using the same frontmatter format as existing commands. Copy to `~/.claude/commands/` to make them global
- **Add new skills**: Drop a `.md` file into `skills/` and reference it from `CLAUDE.md`. See `skills/writing-skills/` for the authoring guide
- **Keep the SDK up to date**: Pull from this repo periodically — your projects get updates automatically via the `@` import:
  ```zsh
  cd /path/to/claude-code-quickstart && git pull
  ```

## Repository Structure

- `.claude/commands/`: Slash command definitions for the development lifecycle.
- `skills/`: Reference guides for specific techniques (TDD, debugging, UI, etc.).
- `docs/plans/`: Where design docs and implementation plans get saved during sessions.
- `agents/`: Subagent definitions used by the build and audit workflows.
- `tests/`: Test suites for verifying skill and workflow behavior.

## Skills

### Core Development
- **`test-driven-development`** - TDD enforcement and patterns (RED-GREEN-REFACTOR)
- **`debugging`** - Root cause analysis and systematic verification
- **`git-ops`** - Git workflows, branching, and worktrees
- **`observability`** - Execution tracing and performance monitoring

### Planning & Design
- **`planning`** (gepetto) - Deep research and specification synthesis for complex features
- **`ui-development`** - Premium UI with design system memory and craft principles

### Quality & Improvement
- **`kaizen`** - Continuous improvement, entropy reduction, and artifact management
- **`writing-skills`** - Skill authoring best practices and natural language output

### Advanced
- **`dispatching-parallel-agents`** - Subagent orchestration for complex tasks

### Specialized Tools

Low-frequency skills for specific use cases. See [skills/specialized/](file:///skills/specialized/SKILL.md) for details.

- **`frontend-slides`** - Zero-dependency HTML presentation generator
- **`image-generator`** - Gemini-powered branded image generation
- **`c4-architecture`** - C4 architecture diagrams for system design
- **`composio-integrations`** - Composio connections to 1000+ external apps

## Troubleshooting

### Slash commands not appearing in terminal autocomplete

If custom slash commands (from `.claude/commands/`) show up in the Mac app but not in the terminal, you likely have multiple Claude Code installations and the terminal is using the wrong one.

**Diagnose:**
```
/doctor
```
Look for "Multiple installations found". If you see both `npm-global` and `native`, the terminal is probably using the npm version.

**Fix — switch to the native install:**
```
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc
```
Open a new terminal tab and verify with `which claude` — it should now point to `~/.local/bin/claude`.

---

*This SDK is Sandhya Simhan's personal quickstart template, created in partnership with **Women Defining AI**, designed to rapidly bootstrap new projects with elite agentic workflows. It merges and optimizes patterns from the original **Claude Code Quickstart** with **Superpowers** ([obra/superpowers](https://github.com/obra/superpowers)), and incorporates community skills curated from [Awesome Claude Skills](https://github.com/BehiSecc/awesome-claude-skills).*

## Third-Party Skills

| Skill | Source | License | Description |
|-------|--------|---------|-------------|
| `frontend-slides` | [zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides) | MIT | Zero-dependency HTML presentation generator with 10 curated visual styles |
| `image-generator` | Internal (blog repo) | — | Gemini-powered branded image generation with customizable brand guidelines |
| `interface-design` | [Dammyjay93/interface-design](https://github.com/Dammyjay93/interface-design) | MIT | Craft-focused UI design with session memory and pattern extraction |

