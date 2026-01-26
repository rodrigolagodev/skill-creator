---
name: skill-creator
description: Expert guidance for creating, structuring, and refining Agent Skills following the open standard. Use when working with skill files, authoring new skills, improving existing skills, or understanding skill architecture and best practices. Use PROACTIVELY when user mentions creating skills, structuring documentation, or building reusable agent capabilities.
license: MIT
compatibility: agent-skills-standard
metadata:
  category: skill-development
  version: "1.1.0"
  author: "Rodrigo Lago"
  standard: "https://agentskills.io"
---

# Creating Agent Skills

Expert system for creating high-quality Agent Skills following the open standard, with comprehensive templates, validation checklists, and best practices.

## What Are Agent Skills?

**Agent Skills** are folders of instructions, scripts, and resources that AI agents can discover and use dynamically to improve their capabilities. Think of them as **plugins for AI agents**.

### Key Benefits

- **Reusable**: Write once, use across multiple agent platforms
- **Discoverable**: Agents can find and activate skills on demand
- **Portable**: Compatible with Claude, OpenCode, Cursor, VS Code, and 20+ platforms
- **Version-controlled**: Skills are just folders → perfect for Git

### The Agent Skills Standard

This skill follows the **[Agent Skills open standard](https://agentskills.io)**, originally developed by Anthropic and adopted by the community.

**Supported platforms:**
- Claude, Claude Code
- OpenCode, Crush
- Cursor, VS Code
- GitHub Copilot
- Gemini CLI, Roo Code, Goose
- And 15+ more...

## Core Principles

### 1. Skills Are Structured Documentation

Skills are **pure markdown documentation** that agents load as context. No executable code required.

```
skill-name/
├── SKILL.md          # Entry point (YAML + Markdown)
├── references/       # Detailed documentation
├── templates/        # Reusable templates
└── workflows/        # Step-by-step guides
```

### 2. YAML Frontmatter + Markdown Body

```yaml
---
name: skill-identifier
description: What it does, when to use, examples
---

# Skill Name

Your instructions here...
```

### 3. Progressive Disclosure

- **SKILL.md**: < 500 lines (quick reference)
- **references/**: Deep dives when needed
- **templates/**: Copy-paste starting points
- **workflows/**: Guided processes

### 4. English-First for LLM Efficiency

Write skills in **English** for optimal LLM performance:
- Faster inference
- Lower token costs
- Better comprehension
- Consistent behavior

## Quick Start

**What would you like to do?**

### Creating a New Skill

Choose your preferred mode:

| Mode | Workflow | Best For |
|------|----------|----------|
| **🧙 Interactive** | [interactive-creation.md](workflows/interactive-creation.md) | First-time creators, complex skills, when unsure |
| **⚡ Automatic** | [create-new-skill.md](workflows/create-new-skill.md) | Experienced users, quick creation, clear requirements |

**Interactive Mode** (Recommended for new users):
```
User: "Quiero crear un skill"
Agent: "¡Vamos paso a paso! ¿Qué problema quieres resolver?"
User: "Analizar código Python"
Agent: "Perfecto. ¿Cómo se llamará? Sugiero: python-analyzer..."
... (continues with guided questions)
```

**Automatic Mode** (For experienced users):
```
User: "Create a skill for analyzing Python code for errors"
Agent: [Creates skill immediately based on description]
```

### Other Actions

- **Validate existing skill** → Use checklist: [validation-checklist.md](references/validation-checklist.md)
- **Understand structure** → Read: [skill-anatomy.md](references/skill-anatomy.md)
- **Copy template** → Start with: [templates/minimal-skill.md](templates/minimal-skill.md)

> **Tip:** When user says "crear skill" or "create a skill" without details, 
> prefer **Interactive Mode** to gather requirements step by step.

**Example - Interactive Flow:**
```
User: "Quiero crear un skill"
    ↓
1. Agent loads skill-creator
2. Agent follows workflows/interactive-creation.md
3. Agent asks: "¿Qué problema resuelve?"
4. User responds, agent confirms
5. Agent asks: "¿Cómo se llamará?"
... (8 phases of guided creation)
4. Agent uses Write tool to create ~/.config/opencode/skills/api-analyzer/SKILL.md
5. Done! Skill is ready to use
```

## Skill Structure

### Required Files

| File | Required | Purpose |
|------|----------|---------|
| `SKILL.md` | ✅ Yes | Entry point with frontmatter + instructions |
| `README.md` | ⚠️ Recommended | GitHub documentation |
| `LICENSE` | ⚠️ Recommended | Open source license (MIT suggested) |

### Optional Directories

| Directory | Purpose | When to Use |
|-----------|---------|-------------|
| `references/` | Detailed documentation | Complex skills with multiple concepts |
| `templates/` | Reusable starting points | Skills that generate content/code |
| `workflows/` | Step-by-step guides | Multi-step processes |
| `examples/` | Complete examples | Show real usage patterns |

### Minimal Skill Example

```yaml
---
name: example-skill
description: >-
  Demonstrates basic skill structure.
  Use when learning how skills work.
  
  <example>
  User: "Show me a skill example"
  Assistant: "I'll use the example-skill."
  </example>
---

# Example Skill

You are a skill demonstrator. Your purpose is to show how skills work.

## Core Instructions

1. Explain what this skill does
2. Provide clear examples
3. Reference additional resources when needed

## When to Use

Use this skill when users ask about:
- How skills are structured
- Skill creation basics
- Agent Skills standard
```

## Frontmatter Specification

See [references/frontmatter-spec.md](references/frontmatter-spec.md) for complete details.

### Required Fields

```yaml
---
name: skill-identifier        # kebab-case, unique
description: >-               # What, when, examples
  What this skill does.
  When to use it.
  
  <example>...</example>
---
```

### Optional Fields

```yaml
---
license: MIT                  # Or Apache-2.0, BSD-3-Clause
compatibility: opencode       # Or agent-skills-standard, claude, cursor
metadata:
  category: development       # Organization
  version: "1.0.0"           # Semantic versioning
  author: "Your Name"
  tags: [python, testing]
---
```

### Description Best Practices

✅ **Good Description:**
```yaml
description: >-
  Analyzes Python code for security vulnerabilities using static analysis.
  Use when reviewing code, auditing projects, or checking for common CVEs.
  
  <example>
  User: "Check this code for security issues"
  Assistant: "I'll use the security-analyzer skill."
  </example>
```

❌ **Bad Description:**
```yaml
description: Helps with security
```

**Rules:**
- Include **WHAT** it does (1 sentence)
- Include **WHEN** to use (triggers)
- Include at least 1 `<example>` block
- Keep under 1024 characters
- Write in third person

## Naming Conventions

### Skill Names (frontmatter `name`)

Use **kebab-case** with descriptive nouns or verb phrases:

✅ **Good:**
- `code-reviewer`
- `api-documentation`
- `database-migration`
- `security-audit`
- `prompt-engineering`

❌ **Avoid:**
- `helper`, `utils`, `tool` (too vague)
- `my-skill`, `skill1` (not descriptive)
- `CodeReviewer` (wrong case)

### Folder Names

Match your skill's `name` field:

```bash
~/.config/opencode/skills/
├── code-reviewer/           # name: code-reviewer
├── api-documentation/       # name: api-documentation
└── security-audit/          # name: security-audit
```

## File Organization

### SKILL.md Structure

```markdown
---
[frontmatter]
---

# Skill Name

Brief introduction (1-2 paragraphs)

## Core Principles

High-level concepts

## Quick Start

How to use this skill

## Main Instructions

Detailed guidance

## When to Use

Triggers and use cases

## References

Links to references/ files

## Examples

Concrete usage examples
```

### References Directory

Break complex topics into separate files:

```
references/
├── core-concepts.md       # Fundamental ideas
├── advanced-patterns.md   # Complex usage
├── anti-patterns.md       # What to avoid
├── validation.md          # Quality checks
└── api-reference.md       # Technical specs
```

**Rule:** Each reference file should be focused on **one topic**.

### Templates Directory

Provide ready-to-use starting points:

```
templates/
├── basic-template.md      # Minimal example
├── advanced-template.md   # Full-featured
└── specialized.md         # Domain-specific
```

**Include variables:** Use `{{VARIABLE}}` or `$VARIABLE` for customization.

### Workflows Directory

Step-by-step processes:

```
workflows/
├── setup.md              # Initial configuration
├── create-x.md           # Creation process
└── troubleshooting.md    # Common issues
```

## Validation Checklist

Before publishing a skill, verify:

- [ ] `SKILL.md` exists with valid YAML frontmatter
- [ ] `name` field is kebab-case and descriptive
- [ ] `description` includes what/when/examples
- [ ] Description has at least one `<example>` block
- [ ] Instructions are clear and actionable
- [ ] Examples demonstrate real usage
- [ ] English language throughout
- [ ] README.md exists (for GitHub)
- [ ] LICENSE file present
- [ ] No executable scripts (pure markdown)

See [references/validation-checklist.md](references/validation-checklist.md) for complete rubric.

## Best Practices

### Do's ✅

1. **Write in English** - Optimal for LLM processing
2. **Use clear descriptions** - What + when + examples
3. **Include examples** - Show real usage with `<example>` blocks
4. **Organize content** - Use references/ for deep dives
5. **Provide templates** - Make it easy to get started
6. **Document limitations** - Be explicit about what skill cannot do
7. **Version your skill** - Use semantic versioning (1.0.0)

### Don'ts ❌

| Anti-Pattern | Problem | Solution |
|--------------|---------|----------|
| No examples | Users don't know when to use | Add `<example>` blocks |
| Vague description | Agent won't activate skill | Specific triggers + use cases |
| Monolithic SKILL.md | Overwhelming (>1000 lines) | Split into references/ |
| Executable scripts | Breaks portability | Pure markdown documentation |
| Missing README | Hard to discover on GitHub | Add README.md |
| No versioning | Breaking changes unclear | Use CHANGELOG.md |

## Skill Creation Process

### Method: Direct File Creation

When creating a skill, use the `Write` tool:

```markdown
1. Understand purpose (ask questions if needed)
2. Read template: templates/minimal-skill.md
3. Customize for specific use case
4. Use Write tool to create: ~/.config/opencode/skills/<name>/SKILL.md
5. (Optional) Add references/, templates/, workflows/ as needed
```

### Guided Workflow

**Two modes available:**

**🧙 Interactive Mode** - [workflows/interactive-creation.md](workflows/interactive-creation.md)
- Ask questions one at a time
- Wait for user responses
- Confirm understanding at each step
- Best for: first-time creators, complex skills

**⚡ Automatic Mode** - [workflows/create-new-skill.md](workflows/create-new-skill.md)
- Create skill from initial description
- No back-and-forth questions
- Best for: experienced users, clear requirements

**Decision Guide:**
```
User says: "Quiero crear un skill" (no details)
→ Use Interactive Mode

User says: "Create a skill for X that does Y and Z"
→ Use Automatic Mode
```

## Success Criteria

A well-structured skill:

- ✅ Has valid YAML frontmatter
- ✅ Description includes triggers and examples
- ✅ Written entirely in English
- ✅ SKILL.md < 500 lines (uses references/ for details)
- ✅ Includes at least 1 usage example
- ✅ Documents what it can and cannot do
- ✅ Has README.md for GitHub discoverability
- ✅ Follows Agent Skills standard

## Reference Documentation

| Document | Description |
|----------|-------------|
| [skill-anatomy.md](references/skill-anatomy.md) | Complete structure breakdown |
| [frontmatter-spec.md](references/frontmatter-spec.md) | YAML specification |
| [validation-checklist.md](references/validation-checklist.md) | Quality verification |

## Templates

| Template | Use Case |
|----------|----------|
| [minimal-skill.md](templates/minimal-skill.md) | Basic skill with TODOs |

## Workflows

| Workflow | Purpose | When to Use |
|----------|---------|-------------|
| [interactive-creation.md](workflows/interactive-creation.md) | 🧙 Guided wizard with prompts | User says "crear skill" without details |
| [create-new-skill.md](workflows/create-new-skill.md) | ⚡ Quick-start guide (index) | User provides full description upfront |
| [skill-discovery-planning.md](workflows/skill-discovery-planning.md) | Phases 1-2: Discovery and Planning | Define purpose and structure |
| [skill-implementation.md](workflows/skill-implementation.md) | Phase 3: Implementation | Create files and content |
| [skill-validation-publishing.md](workflows/skill-validation-publishing.md) | Phases 4-6: Validation, Testing, Publishing | Verify and share |

## Philosophy

> "A great skill is like a well-written manual:
>  - **Clear** about its purpose (description with examples)
>  - **Focused** on one domain (single responsibility)
>  - **Organized** for easy reference (SKILL.md + references)
>  - **Portable** across platforms (Agent Skills standard)
>  - **Documented** for contributors (README + LICENSE)"

Create skills that are **focused**, **clear**, and **reusable**.

## Additional Resources

- **Agent Skills Standard**: https://agentskills.io
- **Anthropic Skills Repo**: https://github.com/anthropics/skills
- **Agent Skills Spec**: https://github.com/agentskills/agentskills
- **OpenCode Docs**: https://opencode.ai/docs/

## Contributing

This skill is open source (MIT). Contributions welcome:
- Report issues
- Suggest improvements
- Share your skills

---

**Version:** 1.1.0  
**Author:** Rodrigo Lago  
**License:** MIT  
**Standard:** Agent Skills (https://agentskills.io)
