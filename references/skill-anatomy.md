# Skill Anatomy

Complete breakdown of Agent Skills structure following the open standard.

## Overview

An **Agent Skill** is a folder containing structured documentation that AI agents can load dynamically to extend their capabilities.

```
skill-name/                    # Root folder (kebab-case)
├── SKILL.md                   # ✅ REQUIRED - Entry point
├── README.md                  # ⚠️  RECOMMENDED - GitHub docs
├── LICENSE                    # ⚠️  RECOMMENDED - Open source license
├── CHANGELOG.md               # ⚠️  RECOMMENDED - Version history
│
├── references/                # 📚 OPTIONAL - Detailed documentation
│   ├── concept-a.md
│   ├── concept-b.md
│   └── api-reference.md
│
├── templates/                 # 📝 OPTIONAL - Reusable templates
│   ├── basic-template.md
│   └── advanced-template.md
│
├── workflows/                 # 🔄 OPTIONAL - Step-by-step guides
│   ├── setup.md
│   └── usage.md
│
└── examples/                  # 💡 OPTIONAL - Complete examples
    ├── example-1/
    └── example-2/
```

---

## 1. SKILL.md (Required)

The **entry point** for your skill. This is the file agents load first.

### Structure

```markdown
---
# YAML Frontmatter (required)
name: skill-identifier
description: What, when, examples
---

# Skill Name

Introduction paragraph

## Core Principles

Fundamental concepts

## Quick Start

How to use immediately

## Main Content

Detailed instructions

## When to Use

Triggers and use cases

## References

Links to references/ files
```

### Size Guidelines

| Size | Recommendation |
|------|----------------|
| **< 500 lines** | ✅ Ideal - Quick to load |
| **500-1000 lines** | ⚠️ Consider splitting into references/ |
| **> 1000 lines** | ❌ Too large - MUST split |

**Why?** Large files slow down context loading and make skills hard to maintain.

### Frontmatter (YAML)

**Required fields:**
```yaml
---
name: skill-identifier        # kebab-case, no spaces
description: >-               # Multi-line, includes examples
  What this skill does.
  When to use it.
  
  <example>
  User: "..."
  Assistant: "I'll use skill-identifier"
  </example>
---
```

**Optional fields:**
```yaml
---
license: MIT
compatibility: agent-skills-standard
metadata:
  category: development
  version: "1.0.0"
  author: "Your Name"
  tags: [python, testing]
---
```

See [frontmatter-spec.md](frontmatter-spec.md) for complete specification.

### Content Structure

```markdown
# Title (H1)

Brief introduction (1-3 paragraphs)

## Section Name (H2)

Main sections

### Subsection (H3)

Detailed breakdowns

## When to Use

- Trigger 1
- Trigger 2
- Trigger 3

## Examples

Concrete usage with code blocks
```

**Best practices:**
- Use standard markdown headings (not XML tags)
- Include code blocks with syntax highlighting
- Add `<example>` blocks in description
- Link to references/ for deep dives

---

## 2. README.md (Recommended)

**Purpose:** Documentation for GitHub/GitLab repositories.

### Structure

```markdown
# Skill Name

Brief description and badges

## Overview

What this skill does

## Installation

```bash
# How to install
```

## Quick Start

Basic usage example

## Features

- Feature 1
- Feature 2

## Documentation

Links to SKILL.md and references/

## Contributing

How to contribute

## License

MIT / Apache / etc.
```

### Why Include README?

- **GitHub discoverability** - First thing users see
- **Installation instructions** - How to add the skill
- **Quick reference** - Overview without opening SKILL.md
- **Professional appearance** - Shows skill is maintained

### Template

```markdown
# {{SKILL_NAME}}

> {{ONE_LINE_DESCRIPTION}}

## Installation

```bash
# Clone to skills directory
git clone https://github.com/{{USER}}/{{REPO}} ~/.config/opencode/skills/{{SKILL_NAME}}
```

## Usage

{{BRIEF_USAGE_EXAMPLE}}

## Documentation

See [SKILL.md](SKILL.md) for complete documentation.

## License

{{LICENSE}} - see [LICENSE](LICENSE) for details.
```

---

## 3. LICENSE (Recommended)

**Purpose:** Legal clarity for open source distribution.

### Recommended Licenses

| License | When to Use |
|---------|-------------|
| **MIT** | Maximum freedom, minimal restrictions |
| **Apache 2.0** | Patent protection, commercial-friendly |
| **BSD-3-Clause** | Similar to MIT with attribution |

### Example: MIT License

```
MIT License

Copyright (c) 2026 Your Name

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

**Get full text:** https://choosealicense.com/licenses/mit/

### Frontmatter Integration

Match your LICENSE file with frontmatter:

```yaml
---
license: MIT    # References LICENSE file
---
```

---

## 4. references/ (Optional)

**Purpose:** Detailed documentation for complex topics.

### When to Use

Use `references/` when:
- SKILL.md exceeds 500 lines
- Topic requires deep technical explanation
- Multiple related concepts need organization
- API/technical specifications needed

### Organization Patterns

#### Pattern 1: By Concept

```
references/
├── core-concepts.md        # Fundamental ideas
├── advanced-patterns.md    # Complex usage
├── troubleshooting.md      # Common issues
└── api-reference.md        # Technical specs
```

#### Pattern 2: By Topic

```
references/
├── installation.md
├── configuration.md
├── authentication.md
└── deployment.md
```

#### Pattern 3: Hybrid

```
references/
├── getting-started.md      # Basics
├── deep-dive/              # Advanced topics
│   ├── architecture.md
│   └── performance.md
└── reference/              # Lookup tables
    ├── api.md
    └── cli-commands.md
```

### File Naming

Use **kebab-case** with descriptive names:
- ✅ `error-handling.md`
- ✅ `database-migrations.md`
- ❌ `ref1.md`
- ❌ `Documentation.md`

### Linking from SKILL.md

```markdown
## Advanced Topics

For detailed information, see:
- [Error Handling](references/error-handling.md)
- [Database Migrations](references/database-migrations.md)
```

---

## 5. templates/ (Optional)

**Purpose:** Ready-to-use starting points for content generation.

### When to Use

Use `templates/` when your skill:
- Generates files (code, configs, docs)
- Provides boilerplate structures
- Offers multiple starting points

### Template Variables

Use placeholders for customization:

**Style 1: Jinja2-style**
```markdown
---
name: {{SKILL_NAME}}
description: {{DESCRIPTION}}
---

# {{SKILL_NAME | title}}
```

**Style 2: Shell-style**
```markdown
---
name: $SKILL_NAME
description: $DESCRIPTION
---

# $SKILL_NAME
```

**Style 3: TODO comments**
```markdown
---
name: my-skill  # TODO: Replace with actual name
description: TODO
---

# TODO: Add skill name here
```

### Examples

#### Basic Template
```markdown
# templates/basic-template.md

---
name: $SKILL_NAME
description: $DESCRIPTION
---

# $SKILL_NAME

TODO: Add introduction

## Instructions

TODO: Add main instructions
```

#### Advanced Template
```markdown
# templates/advanced-template.md

Includes:
- Complete frontmatter
- All sections pre-populated
- Examples and best practices
- References structure
```

---

## 6. workflows/ (Optional)

**Purpose:** Step-by-step guides for processes.

### When to Use

Use `workflows/` for:
- Multi-step procedures
- Setup/installation guides
- Troubleshooting processes
- Complex operations

### Structure

```markdown
# Workflow: {{NAME}}

## Overview

What this workflow accomplishes

## Prerequisites

- Requirement 1
- Requirement 2

## Steps

### Step 1: {{ACTION}}

Description

```bash
# Commands
```

**Expected output:**
```
...
```

### Step 2: {{ACTION}}

...

## Verification

How to confirm success

## Troubleshooting

Common issues and solutions
```

### Examples

- `setup.md` - Initial configuration
- `create-x.md` - Creation process
- `migrate-from-y.md` - Migration guide
- `troubleshooting.md` - Problem solving

---

## 7. examples/ (Optional)

**Purpose:** Complete, working examples.

### When to Use

Use `examples/` for:
- Real-world use cases
- Complete projects
- Integration demos
- Tutorial walkthroughs

### Organization

```
examples/
├── basic-example/
│   ├── README.md
│   ├── input.md
│   └── output.md
│
└── advanced-example/
    ├── README.md
    ├── files/
    └── documentation.md
```

### Example README

```markdown
# Example: {{NAME}}

## Scenario

What this example demonstrates

## Files

- `input.md` - Starting point
- `output.md` - Expected result

## Usage

How to run this example

## Learning Points

- Key concept 1
- Key concept 2
```

---

## 8. CHANGELOG.md (Recommended)

**Purpose:** Version history and change tracking.

### Format

Use [Keep a Changelog](https://keepachangelog.com/) format:

```markdown
# Changelog

## [1.1.0] - 2026-01-25

### Added
- New template: advanced-template.md
- Reference: api-documentation.md

### Changed
- Improved SKILL.md structure
- Updated examples

### Fixed
- Typo in frontmatter-spec.md

## [1.0.0] - 2026-01-20

Initial release
```

---

## File Size Guidelines

| File Type | Ideal Size | Max Size | Action if Exceeded |
|-----------|------------|----------|-------------------|
| SKILL.md | < 500 lines | 1000 lines | Split into references/ |
| References | < 300 lines | 600 lines | Split into sub-topics |
| Templates | < 200 lines | 400 lines | Create variants |
| Workflows | < 400 lines | 800 lines | Split into steps |
| README.md | < 200 lines | 400 lines | Link to docs |

---

## Minimal Skill

**Absolute minimum** for a valid skill:

```
my-skill/
└── SKILL.md
```

```yaml
---
name: my-skill
description: What it does, when to use it.
---

# My Skill

Instructions here...
```

---

## Production-Ready Skill

**Recommended** for public/shared skills:

```
my-skill/
├── SKILL.md                # Core content
├── README.md               # GitHub docs
├── LICENSE                 # MIT/Apache
├── CHANGELOG.md            # Version history
│
├── references/             # 2-5 detailed docs
│   ├── getting-started.md
│   └── advanced.md
│
├── templates/              # 1-3 templates
│   └── basic.md
│
└── workflows/              # 1-2 guides
    └── setup.md
```

---

## Common Mistakes

| Mistake | Problem | Solution |
|---------|---------|----------|
| Monolithic SKILL.md | Too large (>1000 lines) | Split into references/ |
| Missing description | Agents won't activate | Add what/when/examples |
| No examples | Users don't know usage | Add `<example>` blocks |
| Executable scripts | Breaks portability | Use markdown docs |
| Wrong structure | Doesn't follow standard | Follow this anatomy |

---

## Validation

Use [validation-checklist.md](validation-checklist.md) to verify your skill structure.

**Quick checklist:**
- [ ] SKILL.md exists
- [ ] Valid YAML frontmatter
- [ ] name and description present
- [ ] Description has examples
- [ ] SKILL.md < 500 lines (or uses references/)
- [ ] README.md for GitHub
- [ ] LICENSE file present
- [ ] All markdown (no scripts)

---

## References

- **Agent Skills Standard**: https://agentskills.io
- **Anthropic Skills**: https://github.com/anthropics/skills
- **Keep a Changelog**: https://keepachangelog.com/
- **Choose a License**: https://choosealicense.com/
