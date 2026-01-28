# Repository Workflow Best Practices

**Source Repository**: Blog Management Workflow
**Last Updated**: 2025-12-30
**Purpose**: Reusable patterns for content-driven repositories and Claude Code workflows

---

## Table of Contents

1. [Repository Structure](#repository-structure)
2. [Documentation Patterns](#documentation-patterns)
3. [Content Organization](#content-organization)
4. [Writing & Style](#writing--style)
5. [Git Workflow](#git-workflow)
6. [Automation & Configuration](#automation--configuration)
7. [Claude Code Integration](#claude-code-integration)
8. [Quick Start Template](#quick-start-template)

---

## Repository Structure

### Pipeline-Based Organization

Use numbered directories to represent workflow stages:

```
project/
├── 1-ideas/              # Raw concepts and brainstorming
│   ├── IDEAS.md          # Master tracking document
│   └── [supporting-docs].md
├── 2-outlines/           # Structured planning
│   ├── OUTLINE_TEMPLATE.md
│   └── [topic-slug].md
├── 3-drafts/             # Work-in-progress
│   └── [topic-slug].md
├── 4-posts/              # Publication-ready
│   ├── POST_TEMPLATE.md
│   └── [topic-slug].md
├── scripts/              # Automation helpers
├── .claude/              # Claude configuration
│   └── settings.local.json
├── .gitignore
├── WORKFLOW.md           # Process documentation
└── README.md
```

**Key Principles**:
- Numbers force sequential thinking and make status obvious
- Each directory includes a template file for consistency
- Clear progression path from idea to publication
- Templates reduce friction for new entries

### Naming Conventions

- **Ideas**: Tracked in `IDEAS.md` with sections
- **Files**: `[topic-slug].md` format (lowercase, hyphens)
- **Series**: `part-[N]-[slug].md` for multi-part content
- **Supporting docs**: Descriptive names (e.g., `deep-dive-examples-for-background.md`)

---

## Documentation Patterns

### Metadata-First Structure

Every document starts with essential metadata:

```markdown
# [Title]
**Date Created**: YYYY-MM-DD
**Status**: [Outline/Draft/Published]
**Target Word Count**: ~800-1500 words
**Target Audience**: [Specific personas, not generic]
**Estimated Reading Time**: X-Y minutes
**Tags**: #tag1 #tag2 #tag3
```

### Outline Template Structure

```markdown
## Hook / Opening
- [Attention-grabbing narrative or scenario]

## Introduction
- **Problem/Question**:
- **Why it matters**:
- **What readers will learn**:

## Main Content

### Section 1: [Heading]
**Key Point**: [Single sentence core idea]
**Details**:
- [Supporting bullet points]
**Examples/Stories**:
- [Concrete instances]

### Section 2: [Heading]
[Same structure]

### Section 3: [Heading]
[Same structure]

## Conclusion
- **Summary**:
- **Key Takeaways**:
  1. [Numbered list]
- **Call to Action**:

## Research & References
- [Links and sources]

## SEO & Metadata
- **Title**:
- **Meta Description**:
- **Keywords**:
```

### Post Template Elements

- Conversational opening with hooks
- Clear section hierarchy (h2 for major, h3 for sub)
- Visual variety: blockquotes, lists, code blocks
- Key Takeaways section with bold highlights
- Engagement section with CTA
- Publishing checklist (8+ items)

**Design Principle**: Outlines are structural/analytical; posts are narrative/engaging. This represents the ideation-to-publication arc.

---

## Content Organization

### Series Management

**Master Outline Pattern**:
- Create series overview in `1-ideas/`
- Group parts into thematic arcs (e.g., Foundation, Core Concepts, Practical Skills)
- Link to individual part outlines
- Document all running examples and systems

**Cross-Cutting Ideas Document**:
- Maintain `series-ideas-holding-doc.md` in `2-outlines/`
- Track recurring themes that span multiple parts
- Link back to specific parts using the theme
- Single source of truth for patterns

### Target Audience Specificity

**Bad**: "Developers", "Everyone", "Users"

**Good**:
- "No-code/low-code builders using AI tools (Lovable, Replit, Cursor, v0)"
- "Self-taught developers who feel 'something is missing' in technical understanding"
- "Non-engineer builders (founders, product managers, designers who prompt)"

### Real Example Registry

Document actual systems used for examples:

```markdown
## Running Examples Throughout Series

- **Library management system** (checkout, returns, fines)
  - Documented incidents: double-checkout race condition
- **Attendance tracker** (concert check-ins with QR codes)
  - Documented incidents: silent failure, cache sync issues
- **Blog workflow** (idea → outline → draft → publish)
- **Inspiration repo** (RSS → transcription → deduplication → GitHub)
```

**Important**: All examples must be based on actual documented incidents. Do not fabricate specific failure scenarios.

---

## Writing & Style

### Hook Pattern

1. Specific scenario (concrete, relatable, often "2am" moment)
2. Emotion acknowledgment
3. Paradigm shift explanation
4. Promise to reader

Example structure:
```markdown
It's 2am. You need to change [simple thing]. Simple, right?

[Describe the unexpected difficulty and emotion]

You make the change. Something breaks. You're not sure what.

This is the [core feeling this addresses]. Here's why it happens and how to fix it.
```

### Section Development Pattern

For each major section:
- **Key Point**: Single declarative sentence (what they'll learn)
- **Details**: Supporting bullet points with specific examples
- **Examples/Stories**: Real incidents from documented systems
- **Relevance**: Connect back to reader's problem

### Technical Explanation Pattern

1. Plain-language term explanation first
2. Technical analogy/comparison
3. Observable behavior example (what it looks like when it fails)
4. Relevance to builder's problem

**Example**: Instead of "race condition," show: "Five check-ins get lost. Three people get duplicate emails. You refresh frantically. Same code, different results."

---

## Git Workflow

### Commit Message Patterns

**Structure**: `[Action] [Scope]: [Specific change]`

**Good Examples**:
- `Add blog ideas: systems thinking series`
- `Create outline for: invisible curriculum`
- `Enhance technical terminology with comprehensive definitions`
- `Revise Parts 1-4 outlines: Add layman explanations`
- `Publish: understanding-race-conditions`

**Action Verbs**:
- Add, Create, Enhance, Revise, Simplify, Refine
- Update (when comprehensive)
- Fix (for corrections)
- Move (when reorganizing)

### Commit Scope

- **Single file per commit** when possible
- **Related updates batched** (e.g., revising multiple parts for language clarity)
- **Atomic changes** (one logical change per commit)

### Workflow-Specific Commands

```bash
# After adding ideas
git add 1-ideas/IDEAS.md
git commit -m "Add blog ideas: [topic names]"

# After creating outline
git add 2-outlines/your-topic.md
git commit -m "Create outline for: [topic]"

# After drafting
git add 3-drafts/your-topic.md
git commit -m "Draft: [topic]"

# When publishing (move file + update tracking)
git mv 3-drafts/your-topic.md 4-posts/your-topic.md
git add 4-posts/your-topic.md 1-ideas/IDEAS.md
git commit -m "Publish: [topic]"
```

### Progressive Refinement Workflow

Don't expect perfection in creation commits. Use subsequent commits for:
- Language simplification
- Clarity improvements
- Example additions
- Technical term explanations

Each commit message should explain the specific refinement type.

---

## Automation & Configuration

### .gitignore Pattern

Keep it minimal and non-intrusive:

```gitignore
# OS Files
.DS_Store
Thumbs.db

# Editor files
.vscode/
.idea/
*.swp
*.swo
*~

# Personal notes (if private)
# Add specific patterns only as needed
```

Ignore only OS artifacts and editor temp files unless you have specific sensitive data.

### Scripts Directory Structure

```
scripts/
├── README.md           # Document available scripts
├── add-idea.sh         # Interactive idea capture
├── create-outline.sh   # Scaffold from template
└── publish.sh          # Move to 4-posts/, update tracking
```

**Philosophy**:
- Document extension points
- Add scripts as workflow pain points emerge
- Keep scripts simple and single-purpose

### Closeout Process

After completing a milestone, explicitly update:
1. Master outline/tracking document
2. Supporting documents (cross-references)
3. Related files (series-ideas, examples registry)
4. Status indicators in metadata

---

## Claude Code Integration

### .claude/settings.local.json

Restrict available commands to safe operations:

```json
{
  "permissions": {
    "allow": [
      "Bash(git add:*)",
      "Bash(git commit:*)",
      "Bash(git push)",
      "Bash(ls:*)"
    ]
  }
}
```

**Benefits**:
- Enables git workflow automation
- Prevents destructive operations
- Claude can help with commit messages and file movements

### Claude-Friendly Practices

1. **Clear file structure**: Numbered directories make navigation obvious
2. **Template files**: Claude can scaffold new content from templates
3. **Metadata blocks**: Structured data Claude can read and update
4. **Explicit workflow**: WORKFLOW.md documents the process
5. **Example registry**: Claude can reference real systems for consistency

### Common Claude Tasks

- **Idea capture**: Add to IDEAS.md with proper formatting
- **Outline creation**: Scaffold from OUTLINE_TEMPLATE.md
- **Content refinement**: Simplify language, add examples
- **Status updates**: Track completion in metadata
- **Git operations**: Add, commit with descriptive messages
- **Cross-reference updates**: Update series outline when parts complete

---

## Quick Start Template

### For New Content Repositories

1. **Copy directory structure** (numbered pipeline)
2. **Adapt templates** to your content type
3. **Create WORKFLOW.md** documenting your specific process
4. **Set up .claude/settings.local.json** with safe permissions
5. **Initialize git** with minimal .gitignore
6. **Create master tracking document** (IDEAS.md equivalent)

### For New Series/Projects

1. **Create master outline** in `1-ideas/`
2. **Define target audience** (specific personas)
3. **Document running examples** (real systems only)
4. **Scaffold individual outlines** from template
5. **Create cross-cutting ideas doc** if multi-part
6. **Set up tracking checkboxes** for completion

### First-Time Setup Commands

```bash
# Create repository structure
mkdir -p 1-ideas 2-outlines 3-drafts 4-posts scripts .claude

# Copy templates
cp OUTLINE_TEMPLATE.md 2-outlines/
cp POST_TEMPLATE.md 4-posts/

# Create tracking document
touch 1-ideas/IDEAS.md

# Initialize git
git init
echo ".DS_Store\n.vscode/\n*~" > .gitignore
git add .
git commit -m "Initialize repository structure"

# Set up Claude permissions
cat > .claude/settings.local.json << 'EOF'
{
  "permissions": {
    "allow": [
      "Bash(git add:*)",
      "Bash(git commit:*)",
      "Bash(git push)",
      "Bash(ls:*)"
    ]
  }
}
EOF
```

---

## Key Principles Summary

1. **Structure over chaos**: Numbered directories, templates, metadata
2. **Progressive refinement**: Don't expect perfection upfront
3. **Real examples only**: Document actual systems and incidents
4. **Audience-specific**: Write for personas, not generic "users"
5. **Atomic commits**: One logical change per commit, descriptive messages
6. **Template-driven**: Reduce friction with scaffolding
7. **Cross-reference**: Maintain links between series, parts, examples
8. **Closeout process**: Explicitly update all related documents
9. **Minimal automation**: Add scripts as pain points emerge
10. **Claude-friendly**: Clear structure, metadata, explicit workflows

---

## Metrics & Guidelines

**Content Density**:
- Outlines: 200-500 lines (concrete, example-heavy)
- Drafts: 1-2x outline length (narrative expansion)
- Posts: 8-10 minute read (1600-2000 words)

**Metadata Tracking**:
- Status: Brainstorming → Outline → Draft → Published
- Date created/updated
- Target audience (specific)
- Word count range
- Reading time estimate

**Git Activity**:
- Commit frequently (3-4 per active day)
- Descriptive messages (action + scope + change)
- Progressive refinement (multiple commits per file)
- Meta-commits when updating related files

**Series Management**:
- Master outline + individual part outlines
- Cross-cutting ideas document
- Running examples registry
- Thematic arc grouping (Foundation → Core → Practical → Strategic)

---

## Adaptation Guidelines

**For Different Content Types**:
- **Documentation**: Adapt outlines to API/feature structure
- **Code tutorials**: Replace examples with code snippets and repos
- **Research**: Add hypothesis/methodology/results sections
- **Product specs**: Replace writing sections with requirements/designs

**For Different Workflows**:
- Adjust pipeline stages (e.g., 1-backlog, 2-active, 3-review, 4-done)
- Keep numbered structure for clarity
- Maintain templates for each stage
- Document your specific process in WORKFLOW.md

**For Team Repositories**:
- Add CODEOWNERS or assignment tracking
- Document review process
- Add checklist items for peer review
- Include collaboration templates (PR template, issue template)

---

## Additional Resources

**From This Repository**:
- [WORKFLOW.md](WORKFLOW.md) - Detailed process documentation
- [1-ideas/IDEAS.md](1-ideas/IDEAS.md) - Example of master tracking
- [2-outlines/OUTLINE_TEMPLATE.md](2-outlines/OUTLINE_TEMPLATE.md) - Reusable outline structure
- [systems_thinking_for_builders_10_part_series_outline.md](1-ideas/systems_thinking_for_builders_10_part_series_outline.md) - Series management example

**Best Practice Origins**:
- Extracted from 59 commits across active development
- Based on 25 markdown files, 8,364+ lines of content
- Proven through 11-part series management
- Refined through multiple progressive commits

---

**Last Updated**: 2025-12-30
**Repository**: Blog Management Workflow
**License**: Use freely for your projects
