# Sandhya Simhan's Antigravity SDK: Unified Agentic Tooling

A high-performance library of skills and workflows for agentic coding assistants, optimized for the Antigravity IDE. This repository merges the best of **Claude Code Quickstart** and **Superpowers** into a single, unified framework.

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

1. **Read the Manual**: Start with [CLAUDE.md](file:///CLAUDE.md) to understand the operating standards.
2. **Review your History**: Check [PROJECT_HISTORY.md](file:///PROJECT_HISTORY.md) for the latest project context.
3. **Use the Skills**: Explore the [skills/](file:///skills/) directory for atomic "how-to" guides.

## Repository Structure

- `.agent/workflows/`: Unified slash command definitions.
- `skills/`: Atomic reference guides for specific techniques.
- `docs/plans/`: Storage for designs and implementation plans.
- `tests/`: Extensive test suites for verifying agent behavior.

## Workflows

Trigger workflows directly using slash commands in your agentic IDE:

### Core Development Cycle
- `/brainstorm`: Refine an idea into a design with audience research
- `/design`: Create a TDD implementation plan with architectural rigor
- `/implement`: Execute a plan step-by-step with observability
- `/code-review`: Perform a technical quality check and trace review
- `/closeout`: Apply Kaizen improvements, generate changelogs, and finalize history

### Utility Commands
- `/add-bug`: Add a bug to the tracking table without starting work on it
- `/add-feature`: Add a feature request to the implementation plan without starting work on it
- `/add-skills`: Scout and integrate patterns from new repositories
- `/connect`: Bridge to 1000+ external apps via Composio

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

---

*This SDK is Sandhya Simhan's personal quickstart template, created in partnership with **Women Defining AI**, designed to rapidly bootstrap new projects with elite agentic workflows. It merges and optimizes patterns from the original **Claude Code Quickstart** with **Superpowers** ([obra/superpowers](https://github.com/obra/superpowers)), and incorporates community skills curated from [Awesome Claude Skills](https://github.com/BehiSecc/awesome-claude-skills).*

## Third-Party Skills

| Skill | Source | License | Description |
|-------|--------|---------|-------------|
| `frontend-slides` | [zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides) | MIT | Zero-dependency HTML presentation generator with 10 curated visual styles |
| `image-generator` | Internal (blog repo) | — | Gemini-powered branded image generation with customizable brand guidelines |
| `interface-design` | [Dammyjay93/interface-design](https://github.com/Dammyjay93/interface-design) | MIT | Craft-focused UI design with session memory and pattern extraction |

