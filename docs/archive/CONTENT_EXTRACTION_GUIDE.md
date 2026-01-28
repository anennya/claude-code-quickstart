# Content Extraction Guide

**Purpose:** Turn your project learnings into blog posts and LinkedIn content

This guide shows you how to extract publishable content from the patterns and insights you've documented in your projects.

---

## Why Your Project Learnings Make Great Content

Every time you build something and document it properly (in PROJECT_HISTORY.md and CLAUDE.md), you create:

1. **Real-world examples** - Not theoretical advice
2. **Before/after comparisons** - Tangible improvements
3. **Concrete implementations** - Code, YAML, actual files
4. **Lessons learned** - Hard-won insights from production use

This is exactly what readers want: practical knowledge from someone who's actually built it.

---

## 20+ Ready-to-Write Topics

These topics are extracted directly from patterns in [CLAUDE.md](CLAUDE.md) and [BEST_PRACTICES.md](BEST_PRACTICES.md):

### Technical Deep Dives (800-1200 words)

1. **"Metadata-Driven Automation: Tag Once, Query Forever"**
   - Example: Recipe tagging (no_chop_compatible, effort_level, main_veg)
   - How rich metadata enables smart filtering
   - When to invest in metadata upfront vs. later

2. **"When to Graduate from Plain Text to Databases"**
   - The ~10k records threshold
   - 234 recipes in YAML: why it worked perfectly
   - Tradeoffs: simplicity vs. performance
   - Decision framework

3. **"Validation Patterns: Catching Errors Before They Propagate"**
   - Validation scripts structure
   - Checklist-based validation
   - When to run: before commit, after generation, in CI/CD
   - Example: Meal planner validation caught malformed YAML

4. **"State Tracking in Multi-Step Workflows"**
   - Append-only history pattern
   - Idempotent operations
   - Resumability after interruptions
   - Example: Blog workflow staged pipeline

5. **"Git-Friendly Data Structures"**
   - Why YAML > JSON > databases (for certain use cases)
   - Line-by-line change tracking
   - Merge conflict management
   - When Git-friendly stops mattering

### Philosophical/Process (600-900 words)

6. **"Design for Your Worst Day, Not Your Best Day"**
   - Energy-based scheduling origin story
   - Friday evening cooking → bedtime chaos
   - Solution: No-chop recipes only on Friday
   - Broader application: design systems for depleted state

7. **"Constraints Create Freedom: The Paradox of Limits"**
   - Decision paralysis problem
   - How limiting options reduced stress
   - Examples: "5-9pm device-free", "Friday = low effort only"
   - Applying to other domains (content creation, product features)

8. **"Use It Before Automating It: Why Manual-First Works"**
   - Weeks 1-3: Manual meal planning
   - Week 4: Noticed repetition → built history tracking
   - Week 8: Automated vegetable proposals
   - Real usage reveals actual needs vs. imagined ones

9. **"Progressive Refinement Over Perfection"**
   - Multiple commits improving same file
   - Blog workflow: outline → draft → refinement → refinement → published
   - Why this beats trying to get it right first time
   - Cultural shift: commit history shows iteration, not failure

10. **"The Power of Append-Only History"**
    - Why NEVER overwrite history files
    - Enables anti-repetition without manual tracking
    - Audit trail and debugging
    - Psychological benefit: progress is visible

### Practical Patterns (1000-1500 words)

11. **"The Anti-Repetition Pattern: Ensuring Variety Without Manual Tracking"**
    - Problem: Manual tracking is exhausting
    - Solution: Append-only history + filtering
    - Implementation: Load last N records, filter, select
    - Example: "No recipe from last 3 weeks"
    - Extensions: Track templates AND instances

12. **"Energy-Based Scheduling: Matching Tasks to Capacity"**
    - Variable effort tasks + variable human capacity
    - Metadata structure: effort_level (low/normal/high)
    - Schedule structure: day → energy → suitable_for
    - Example: Monday batch cooking, Friday reheating only
    - Beyond meal planning: content creation, deep work scheduling

13. **"Template + Variation: Managing Categories with Instances"**
    - Problem: Too much variety → chaos; too little → boring
    - Solution: Track category (template) and instance (specific item)
    - Constraints: "Max 2 tacos per week" (even if different recipes)
    - Application: Blog post templates, code patterns, design systems

14. **"Staged Pipelines: Making Progress Visible"**
    - Numbered folders: 1-ideas, 2-outlines, 3-drafts, 4-published
    - Status is obvious from location
    - Benefits: Easy to see what's in flight, clear progression
    - Use git mv to move between stages (preserves history)
    - Example: Managing 11-part blog series cleanly

15. **"Validation Scripts: Your Safety Net"**
    - When to create: Complex constraints, easy to violate
    - What to check: Required fields, enum values, business rules
    - Where to run: Pre-commit hooks, post-generation, CI/CD
    - Example validation function structure
    - ROI: Catches errors before they become user-facing bugs

### Git & Documentation (500-800 words)

16. **"Writing Commit Messages That Tell a Story"**
    - Good: `Add energy-based prep model: Monday batch cooking, Friday no-prep`
    - Bad: `update stuff`, `fix bug`
    - Format: [Action] [Scope]: [Specific change]
    - Include rationale in body when helpful
    - Example: 6 months later, you'll thank yourself

17. **"Documentation as You Go: The PROJECT_HISTORY.md Pattern"**
    - Why retroactive documentation fails
    - Session template: What built, key decisions, challenges, learnings
    - Git commit references anchor timeline
    - Example: Meal planner 13 phases documented in real-time

18. **"Atomic Commits: One Logical Change, One Commit"**
    - What counts as "atomic"
    - When to batch vs. separate
    - Benefits: Easy revert, clear history, better code review
    - Examples from blog workflow: single file per commit vs. related batch

### AI/Claude-Specific (700-1000 words)

19. **"CLAUDE.md: Teaching AI Your Project's Rules"**
    - Why baking knowledge into a file beats remembering
    - Structure: Role, Files to Read/Write, Rules, Validation, Error Handling
    - Example: "No recipe from last 3 weeks" → Claude checks every time
    - Universal patterns vs. domain-specific customization

20. **"Validation Checklists: How to Make AI Reliable"**
    - Problem: AI can skip steps if not explicit
    - Solution: Detailed checklist in CLAUDE.md
    - Example: 12-item validation before finalizing meal plans
    - Pattern: Before writing output, verify ALL of these

21. **"Error Handling for AI Systems: 4 Scenarios You Must Cover"**
    - Missing required information (don't fabricate!)
    - Constraint conflicts (explain math, suggest alternatives)
    - Invalid input values (reference taxonomy, give examples)
    - Data unavailable (don't proceed, provide template)

22. **"Structured Data > Unstructured Text for AI"**
    - YAML/JSON enables smart decisions
    - Metadata queryability
    - Validation becomes possible
    - Example: Filtering recipes by attributes

---

## Content Extraction Template

Use this structure for any pattern you want to write about:

### Hook (1-2 paragraphs)

**Pattern: "It's 2am..." scenario**

Set the scene with a specific, relatable problem moment:

```markdown
It's Friday night. You're exhausted from the week. You start chopping vegetables for dinner.

30 minutes later, you're still chopping. The kitchen is a mess. Your kids need help with bedtime. You're stressed.

This is when you realize: your meal planning system is optimized for your best days, not your worst days.

Here's how I redesigned it - and why you should design all your systems for depletion, not peak energy.
```

### The Problem (2-3 paragraphs)

- What was broken or inefficient?
- What was the cost (time, stress, quality)?
- What prompted you to solve it?

**Example:**
```markdown
For weeks 1-3, I manually planned meals every Sunday. By week 4, I noticed I was accidentally repeating recipes. I'd think "Haven't used this recently" and be wrong.

Manual tracking was exhausting. I tried a spreadsheet. I'd forget to update it. The whole point of meal planning was to reduce cognitive load, but tracking added more.

I needed a system that remembered for me.
```

### The Insight (1-2 paragraphs)

- What did you realize?
- What principle emerged?
- What was the "aha moment"?

**Example:**
```markdown
The insight: If I track history automatically (append-only file), I can filter against it programmatically. No manual "did I use this recently?" checking.

Tag once (in history file), filter forever (in selection logic).

This is metadata-driven automation: upfront structure enables downstream intelligence.
```

### The Solution (3-5 paragraphs with code/YAML examples)

- How did you implement it?
- Show actual code, YAML, file structure
- Walk through the logic

**Example:**
```markdown
Created `data/history.yml`:

```yaml
weeks:
  - week_of: 2025-12-23
    dinners:
      - recipe_id: "lentil_tacos_001"
        day: "mon"
  - week_of: 2025-12-16
    dinners:
      - recipe_id: "lentil_tacos_001"
        day: "wed"
```

Selection logic (in CLAUDE.md):

```markdown
Before selecting recipes:
1. Load data/history.yml
2. Extract all recipe_ids from last 3 weeks
3. Filter those from available recipes
4. Select only from remaining
```

Simple. No database. Git-trackable. Human-readable.
```

### The Results (2-3 paragraphs)

- What improved? (Qualitative and quantitative)
- What worked well?
- What was surprising?

**Example:**
```markdown
Zero repeated recipes in 12 weeks. Zero manual tracking.

Unexpected benefit: history file became meal planning journal. Could see "oh, I eat a lot of tacos" - insights I didn't have before.

Cost: 5 minutes upfront to structure history file. Payoff: Every subsequent week was easier.
```

### How You Can Use This (3-5 bullet points)

Actionable steps for reader to apply the pattern:

```markdown
## How You Can Use This

1. **Identify repetitive decisions** in your workflow (What do you choose manually each time?)

2. **Create append-only history file**
   ```yaml
   records:
     - timestamp: "2025-01-15"
       selected_items: ["item_a", "item_b"]
   ```

3. **Add filtering logic** (Load history → Extract last N → Filter available options)

4. **Test with small window** (Start with "last 5" not "last 20" - easier to debug)

5. **Expand as confidence grows** (Once working, increase lookback window)
```

### Key Takeaways (3-5 bullet points)

Summarize main points - readers often skim to this section:

```markdown
## Key Takeaways

- **Manual tracking doesn't scale** - Offload to structured data
- **Append-only history is powerful** - Enables smart filtering without databases
- **Metadata upfront, automation forever** - Tag once, query repeatedly
- **Start small, expand gradually** - Test pattern before full commitment
- **Git-friendly formats win** - YAML > database for this scale
```

---

## Blog Post vs. LinkedIn Post

### Blog Post (800-1500 words)

- Full template above
- Code examples with syntax highlighting
- Multiple sections with H2/H3 hierarchy
- Detailed implementation steps
- 8-10 minute read

**Best for:**
- Technical deep dives
- Practical patterns with code
- "How I built X" stories

### LinkedIn Post (200-400 words)

- Hook + Problem + Insight + Key Takeaway
- Skip the detailed implementation
- Focus on the principle, not the code
- Link to blog for full version

**Template:**

```markdown
[HOOK - 1-2 sentences]

[PROBLEM - 2-3 sentences]

[INSIGHT - 2-3 sentences]

[KEY TAKEAWAY - 3-5 bullet points]

---

[If you want the technical details (code, YAML examples), I wrote a full guide here: [link]]
```

**Example:**

```markdown
Your meal planning system breaks down on Friday night. You're exhausted, the kids need help, and you're chopping vegetables for 30 minutes.

This is when I realized: I'd optimized for my best days, not my worst days. My system assumed peak energy, but life doesn't work that way.

The fix: Energy-based scheduling. Friday = low-effort meals only (no chopping required). Monday = high-energy day (batch cooking allowed).

Key insights:

• Design systems for depletion, not peak state
• Variable capacity requires variable task complexity
• Constraints (Friday = low effort) reduce stress, don't add it
• This applies beyond meal planning: content creation, deep work scheduling, project planning

6 months later, zero Friday cooking stress. The system works because it matches my reality, not my ideal.

---

Full implementation (with YAML examples, validation logic, and code): [link]
```

---

## Content Calendar Strategy

### Frequency

- **Blog**: 1-2 per month (in-depth, evergreen)
- **LinkedIn**: 1-2 per week (quick insights, teasers for blog)

### Sequencing

1. **Week 1**: Publish blog post (e.g., "Anti-Repetition Pattern")
2. **Week 1**: LinkedIn post (hook + key takeaway, link to blog)
3. **Week 2**: LinkedIn post (different angle on same topic, e.g., "Why manual tracking fails")
4. **Week 3**: LinkedIn post (related topic, e.g., "Append-only history pattern")
5. **Week 4**: Next blog post (e.g., "Energy-Based Scheduling")

### Repurposing Matrix

One blog post → Multiple LinkedIn posts:

**Example: "Anti-Repetition Pattern" blog**

LinkedIn posts you can extract:
1. The problem (manual tracking exhaustion)
2. The solution (append-only history)
3. The unexpected benefit (meal planning journal insight)
4. The broader principle (metadata-driven automation)
5. The "how to apply it" (practical steps)

---

## Hook Patterns That Work

### 1. The "2am Scenario"

```markdown
It's 2am. You need to change [simple thing]. Simple, right?

[Describe unexpected difficulty]

You make the change. Something breaks. You're not sure what.
```

### 2. The "Weeks 1-3 vs Week 4"

```markdown
Weeks 1-3: [You do manual process]

Week 4: [You notice pattern/problem]

Week 8: [You automate the painful part]
```

### 3. The "I Thought X, But Actually Y"

```markdown
I thought adding constraints would make the system rigid.

Actually, constraints reduced decision paralysis and made me more creative within boundaries.

Here's why...
```

### 4. The "Cost: X Minutes, Payoff: Forever"

```markdown
I spent 10 minutes creating a structured history file.

That 10 minutes has saved me hours every week for 3 months.

Here's the pattern...
```

### 5. The "Nobody Tells You This"

```markdown
Nobody tells you that meal planning breaks down on Friday nights.

Every system design tutorial assumes peak energy. But Friday after a long week? You're depleted.

Here's how to design for depletion...
```

---

## SEO Keywords to Target

For discoverability, include these in titles/headers/content:

### Technical Keywords
- "YAML vs database"
- "Git-friendly data structures"
- "Append-only history pattern"
- "Metadata-driven automation"
- "Validation scripts"
- "Idempotent operations"
- "State tracking"

### Process Keywords
- "Progressive refinement"
- "Manual-first automation"
- "Energy-based scheduling"
- "Constraint-based design"
- "Anti-repetition pattern"

### AI/Claude Keywords
- "Claude Code best practices"
- "AI system design"
- "CLAUDE.md tutorial"
- "Structured prompts"
- "AI validation patterns"

---

## Checklist: Before Publishing

### Content Quality
- [ ] Hook grabs attention (specific scenario, relatable problem)
- [ ] Problem is clear (cost, pain point, why it matters)
- [ ] Solution is detailed (code/YAML examples, actual implementation)
- [ ] Results are concrete (qualitative + quantitative improvements)
- [ ] Takeaways are actionable (reader can apply immediately)

### Technical Accuracy
- [ ] Code examples work (tested, not pseudo-code)
- [ ] YAML is valid (no syntax errors)
- [ ] File paths are correct
- [ ] Commands run without errors
- [ ] Links work

### Readability
- [ ] Paragraphs are short (2-4 sentences max)
- [ ] Headers break up text (H2 every 200-300 words)
- [ ] Code blocks have syntax highlighting
- [ ] Bullet points for scanability
- [ ] Bold for key terms

### SEO
- [ ] Title includes target keyword
- [ ] Meta description 150-160 characters
- [ ] Alt text on images
- [ ] Internal links to related posts
- [ ] External links to authoritative sources

### Engagement
- [ ] Call to action at end (comment, share, link to related content)
- [ ] Invitation for questions
- [ ] Link to related posts or GitHub repos
- [ ] Social sharing buttons

---

## Example: Full Blog Post

See [example-blog-post.md](example-blog-post.md) for a complete worked example using the template above.

---

## Tools & Resources

### Writing
- **Markdown editors**: Typora, iA Writer, VS Code
- **Grammar**: Grammarly, Hemingway App
- **Readability**: Hemingway App (aim for grade 8-10)

### SEO
- **Keyword research**: Google Trends, AnswerThePublic
- **Meta tags**: Yoast (WordPress), manual HTML
- **Analytics**: Google Analytics, Plausible

### Publishing Platforms
- **Blog**: Medium, Dev.to, Hashnode, personal site
- **LinkedIn**: Native posts (not articles - better algorithm reach)
- **Twitter/X**: Thread format for longer content

### Code Formatting
- **Syntax highlighting**: Prism.js, Highlight.js
- **GitHub Gists**: For embeddable code snippets
- **Carbon**: Beautiful code screenshots

---

## Questions to Ask Yourself

Before extracting content from a pattern:

1. **Have I actually used this in production?** (Not just theory)
2. **Can I show concrete before/after?** (Tangible improvements)
3. **Do I have real code/YAML examples?** (Not pseudo-code)
4. **What did I learn that surprised me?** (Novel insights)
5. **Can someone apply this in 30 minutes?** (Actionable)

If yes to all 5 → You have a blog post.

---

## Final Tips

1. **Write for your past self** - What would have helped you 6 months ago?
2. **Show your work** - Commit history, actual files, real examples
3. **Embrace iteration** - Published isn't finished; you can update
4. **Track what resonates** - Analytics show which topics to expand
5. **Build in public** - Document as you build, not after

Your project learnings are valuable. Extract them. Share them. Help others avoid the struggles you solved.

---

**Next Steps:**

1. Choose a topic from the list above
2. Pull up your PROJECT_HISTORY.md for that pattern
3. Use the content extraction template
4. Write the hook
5. Keep going

You've done the hard part (building and documenting). Now share it.

---

**Last Updated:** 2025-12-30
**Template Version:** 1.0.0
