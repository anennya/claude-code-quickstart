# Claude Code Quickstart

**A battle-tested starter pack for AI-assisted development projects**

This repo consolidates learnings from multiple production projects into a ready-to-clone template. Duplicate it, customize CLAUDE.md, and start building with proven patterns baked in.

---

## What This Gives You

When you duplicate this repo, you get:

1. **[CLAUDE.md](CLAUDE.md)** - AI operating manual with 7 core principles, 5 proven patterns, and comprehensive error handling
2. **[PROJECT_HISTORY.md](PROJECT_HISTORY.md)** - Template for documenting development timeline and learnings
3. **[BEST_PRACTICES.md](BEST_PRACTICES.md)** - Reference guide from blog workflow project (staged pipelines, git practices, Claude integration)
4. **[QUICKSTART_TEMPLATE.md](QUICKSTART_TEMPLATE.md)** - Detailed template for various project types (data processing, content generation, automation)

---

## Quick Start (3 Steps)

### 1. Duplicate This Repo

```bash
# Clone or download
git clone https://github.com/yourusername/claude-code-quickstart.git my-new-project
cd my-new-project
rm -rf .git
git init
```

### 2. Customize CLAUDE.md

Open [CLAUDE.md](CLAUDE.md) and replace **[CUSTOMIZE]** sections:

- **Your Role**: What is this project building?
- **Files to Read**: What context files exist?
- **Files to Write**: What outputs does it generate?
- **Critical Rules**: What constraints must never be violated?
- **Domain-Specific Constraints**: What makes a valid output in your domain?

All the proven patterns (anti-repetition, energy-based scheduling, validation, etc.) stay as-is.

### 3. Start Building

```bash
# Create your project structure (example)
mkdir -p data inputs outputs scripts templates

# Initial commit
git add .
git commit -m "Initialize from claude-code-quickstart template v2.0"
```

Open in VS Code with Claude Code extension and you're ready to go.

---

## What Makes This Different

### 1. Learnings Are Baked Into CLAUDE.md

Instead of you remembering best practices, Claude reads them from CLAUDE.md at the start of every task.

**7 Core Principles:**
- Design for failure modes (fallbacks, validation, idempotency)
- Use plain text until you can't (~10k records threshold)
- Metadata enables intelligence (tag once, query forever)
- Progressive refinement over perfection
- Constraints create freedom
- Documentation as you go
- Atomic commits with context

**5 Proven Patterns:**
- Anti-repetition (avoid repeated selections via history tracking)
- Energy-based scheduling (match task effort to user capacity)
- Template + variation (manage categories with instances)
- Staged pipelines (numbered folders for workflow stages)
- Validation scripts (catch errors before they propagate)

### 2. Real Examples, Not Theory

Every pattern includes:
- When to use it
- How to implement it
- Code/YAML examples
- Real-world origin story (meal planner, blog workflow)

**Example**: The anti-repetition pattern came from meal planning - needed to ensure no recipe repeated within 3 weeks without manual tracking.

### 3. Error Handling Built In

CLAUDE.md includes 4 detailed error scenarios with exact response templates:
- Missing required information
- Constraint conflicts
- Invalid input values
- Data unavailable

Claude knows how to explain problems clearly and suggest alternatives instead of proceeding with invalid outputs.

### 4. Content Extraction Ready

Your project learnings = blog/LinkedIn content.

CLAUDE.md includes:
- 15+ proven content topics extracted from patterns
- Content extraction template (Problem → Insight → Solution → Results → Takeaways)
- Hook patterns ("It's 2am and..." scenarios)

---

## File Guide

### Core Files (Always Present)

| File | Purpose | Customize? |
|------|---------|-----------|
| [CLAUDE.md](CLAUDE.md) | Operating manual Claude reads | Yes - [CUSTOMIZE] sections |
| [README.md](README.md) | Project overview (this file) | Yes - entire file |
| [PROJECT_HISTORY.md](PROJECT_HISTORY.md) | Development timeline template | Yes - track your sessions |
| .gitignore | Standard exclusions | Yes - add domain-specific |

### Reference Files (Read as Needed)

| File | What's Inside | When to Use |
|------|---------------|-------------|
| [BEST_PRACTICES.md](BEST_PRACTICES.md) | Blog workflow patterns (staged pipelines, git practices, Claude integration) | Building content pipelines or wanting detailed git workflow examples |
| [QUICKSTART_TEMPLATE.md](QUICKSTART_TEMPLATE.md) | Detailed template with 3 project archetypes (data processing, content generation, automation) | Starting new project and want comprehensive setup guide |

### Optional Structure (Create as Needed)

```
your-project/
├── data/                 # Source of truth (taxonomy, history, core data)
├── inputs/               # User inputs (ephemeral, per session)
├── outputs/              # Generated files (reproducible from inputs)
├── scripts/              # Automation and validation
└── templates/            # Output format templates
```

See [CLAUDE.md](CLAUDE.md) "Repository Structure Best Practices" for folder decision tree.

---

## Common Use Cases

### Data Processing Pipeline

- **Input**: CSV/JSON data files
- **Output**: Reports, visualizations, summaries
- **Patterns to use**: Anti-repetition (if recurring), validation scripts, staged pipeline
- **See**: [QUICKSTART_TEMPLATE.md](QUICKSTART_TEMPLATE.md) "Template 1: Data Processing Pipeline"

### Content Generation System

- **Input**: Topics, briefs, parameters
- **Output**: Blog posts, documentation, marketing copy
- **Patterns to use**: Anti-repetition (topic variety), staged pipeline (idea → outline → draft → published), template + variation
- **See**: [BEST_PRACTICES.md](BEST_PRACTICES.md) "Pipeline-Based Organization" and [QUICKSTART_TEMPLATE.md](QUICKSTART_TEMPLATE.md) "Template 2: Content Generation System"

### Automation Workflow

- **Input**: Configuration, triggers
- **Output**: Execution results, state tracking
- **Patterns to use**: Energy-based scheduling (if task effort varies), validation scripts, state tracking
- **See**: [QUICKSTART_TEMPLATE.md](QUICKSTART_TEMPLATE.md) "Template 3: Automation Workflow"

---

## How to Use This Repo

### For Starting New Projects

1. Duplicate this repo for each new project
2. Keep [CLAUDE.md](CLAUDE.md) - just customize [CUSTOMIZE] sections
3. Replace [README.md](README.md) entirely with your project details
4. Use [PROJECT_HISTORY.md](PROJECT_HISTORY.md) template to track sessions
5. Reference [BEST_PRACTICES.md](BEST_PRACTICES.md) and [QUICKSTART_TEMPLATE.md](QUICKSTART_TEMPLATE.md) as needed

### For Extracting Blog/LinkedIn Content

See [CLAUDE.md](CLAUDE.md) "Content Creation Reference" section for:
- 15+ proven topic ideas from your patterns
- Content extraction template
- Hook patterns and structure

**Example topics you can write:**
- "Design for Your Worst Day, Not Your Best Day"
- "Metadata-Driven Automation: Tag Once, Query Forever"
- "When to Graduate from Plain Text to Databases"
- "The Anti-Repetition Pattern: Ensuring Variety Without Manual Tracking"

### For Learning Patterns

Read through:
1. [CLAUDE.md](CLAUDE.md) "Common Patterns You Should Know" - 5 battle-tested patterns with implementation details
2. [BEST_PRACTICES.md](BEST_PRACTICES.md) - Blog workflow specific practices (staged pipelines, series management, cross-referencing)
3. [QUICKSTART_TEMPLATE.md](QUICKSTART_TEMPLATE.md) - Comprehensive guide with 3 project archetypes

---

## What Makes These Patterns Work

### Origin Stories

**Meal Planner System** (13 development phases, 3 months production use)
- 234 recipes in YAML (plain text worked perfectly)
- Anti-repetition pattern (no recipe within 3 weeks)
- Energy-based scheduling (Friday = low energy = no-chop only)
- Validation scripts caught malformed YAML
- Key insight: "Design for worst day, not best day"

**Blog Management Workflow** (11-part series)
- Staged pipeline (1-ideas → 2-outlines → 3-drafts → 4-published)
- Target audience specificity (not "developers", but "no-code builders using AI tools")
- Real examples only (documented systems, no fabrication)
- Progressive refinement (multiple commits improving language/clarity)
- Key insight: "Status should be obvious from file location"

### Why Plain Text Works

- Git tracks changes line-by-line
- Human readable and editable
- No database setup or migrations
- Works until ~10k records
- Zero dependencies

**When to graduate:** Complex queries, concurrent users, or performance matters more than simplicity.

---

## Best Practices Summary

### Project Management

1. **Use it before automating it** - Manual process reveals actual pain points
2. **Document as you go** - Update PROJECT_HISTORY.md after every session
3. **Atomic commits** - One logical change, descriptive message
4. **Start minimal** - Add structure as patterns emerge

### Working with Claude Code

1. **Be specific** - "No recipe from last 3 weeks" > "keep it varied"
2. **Provide checklists** - Claude runs through every validation item
3. **Use structured data** - YAML/JSON > unstructured text
4. **Update CLAUDE.md** - Patterns here apply consistently

### Technical Implementation

1. **Design for failure** - Fallbacks, validation, idempotency
2. **Validate early, often** - Before committing, after generating, in CI/CD
3. **Separate concerns** - data/ (source of truth), outputs/ (reproducible)
4. **Tag once, query forever** - Front-load metadata work

---

## Examples of Good vs. Bad

### Good CLAUDE.md Rule

```markdown
- [ ] No recipe can appear in last 3 weeks (check data/history.yml)
- [ ] Thursday/Friday dinners must have no_chop_compatible: true
```

**Why**: Specific, checkable, references exact files

### Bad CLAUDE.md Rule

```markdown
- [ ] Make good meal plans
- [ ] Be creative
```

**Why**: Vague, not actionable, no validation criteria

### Good Commit Message

```
Add energy-based prep model: Monday batch cooking, Friday no-prep

- Recipes tagged with effort_level: low/normal/high
- Friday schedule only allows low-effort recipes
- Monday can handle batch cooking (high energy day)

This addresses evening stress from Friday cooking sessions
bleeding into bedtime routines.
```

**Why**: Clear action, specific changes, includes rationale

### Bad Commit Message

```
update stuff
fix bug
changes
```

**Why**: No context, future you won't know what changed or why

---

## FAQ

**Q: Do I keep all these files when I start a new project?**

A: Keep [CLAUDE.md](CLAUDE.md) (customize it), [PROJECT_HISTORY.md](PROJECT_HISTORY.md) (track your sessions), and .gitignore. Replace [README.md](README.md) entirely with your project details. Use [BEST_PRACTICES.md](BEST_PRACTICES.md) and [QUICKSTART_TEMPLATE.md](QUICKSTART_TEMPLATE.md) as reference - delete them if they're not helpful.

**Q: How much of CLAUDE.md should I customize?**

A: Only the **[CUSTOMIZE]** sections (Your Role, Files to Read/Write, Domain-Specific Constraints). Keep all the Universal Best Practices and Common Patterns - they apply to every project.

**Q: When should I add data/, inputs/, outputs/ folders?**

A: See [CLAUDE.md](CLAUDE.md) "Folder Decision Tree". TL;DR: Start with just README and CLAUDE.md. Add folders when patterns emerge. Don't pre-build structure you don't need yet.

**Q: Can I use this for non-coding projects?**

A: Yes! The patterns work for any structured workflow. Examples: content creation, research synthesis, project planning, documentation. The principles (validation, constraints, metadata, progressive refinement) apply universally.

**Q: How do I extract blog content from my learnings?**

A: See [CLAUDE.md](CLAUDE.md) "Content Creation Reference". It includes 15+ proven topics and a content extraction template (Problem → Insight → Solution → Results → Takeaways).

---

## Contributing

Found a pattern worth adding? Create an issue or PR.

**Criteria for new patterns:**
- Used in production (not theoretical)
- Solves specific problem (not general advice)
- Includes implementation details (not just description)
- Has concrete example (not abstract)

---

## Version History

**v2.0.0** (2025-12-30)
- Consolidated learnings from meal planner + blog workflow
- Created comprehensive [CLAUDE.md](CLAUDE.md) with baked-in best practices
- Added content extraction templates
- 7 core principles, 5 proven patterns, 4 error scenarios

**v1.0.0**
- Initial template from meal planner project

---

## License

Use freely for your projects. No attribution required, but appreciated.

---

**Start simple. Build incrementally. Document continuously.**

Duplicate this repo and start your next project with proven patterns baked in.
