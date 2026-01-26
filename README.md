# Skill Creator

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/standard-Agent%20Skills-orange.svg)](https://agentskills.io)

> Expert system for creating, structuring, and validating Agent Skills following the open standard that works across 20+ platforms.

---

## Overview

The **skill-creator** skill provides everything you need to build high-quality Agent Skills:

- **Ready-to-use template** with TODO placeholders
- **Reference documentation** for structure, frontmatter, and validation
- **Step-by-step workflow** for creating skills from scratch
- **Validation checklist** with scoring rubric
- **Best practices** and anti-patterns guide

This skill follows the professional approach: **pure documentation that the LLM uses as context**, no external scripts or dependencies required.

---

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Skill Structure](#skill-structure)
- [Validation](#validation)
- [Best Practices](#best-practices)
- [Reference Documentation](#reference-documentation)
- [Contributing](#contributing)
- [Changelog](#changelog)
- [License](#license)

---

## Features

| Feature | Description |
|---------|-------------|
| **Minimal Template** | Pre-configured skill template with TODOs |
| **Frontmatter Spec** | Complete YAML specification with all fields |
| **Skill Anatomy** | Deep dive into structure and organization |
| **Validation Checklist** | Field-by-field verification guide |
| **Creation Workflow** | Step-by-step guide from discovery to publishing |
| **Best Practices** | Do's, don'ts, and anti-patterns |

---

## Installation

### Clone the Repository

```bash
git clone https://github.com/rodrigolagodev/skill-creator.git ~/.config/opencode/skills/skill-creator
```

### Verify Installation

```bash
ls ~/.config/opencode/skills/skill-creator/SKILL.md
```

### Other Platforms

| Platform | Installation Path |
|----------|-------------------|
| Claude Desktop | `~/Library/Application Support/Claude/skills/skill-creator` |
| Claude Code | `~/.claude/skills/skill-creator` |
| Cursor | `.cursor/skills/skill-creator` |
| VS Code | `.vscode/skills/skill-creator` |

### Requirements

- **No additional dependencies** - Pure markdown documentation

---

## Quick Start

### 1. Load the Skill

The skill is loaded automatically when needed. Ensure your agent has the `skill` tool enabled:

```yaml
tools:
  skill: true
```

### 2. Create Your First Skill

Ask your assistant:

```
Create a skill for reviewing API documentation
```

The assistant will:
1. Load this skill for guidance
2. Read the template from `templates/minimal-skill.md`
3. Create `~/.config/opencode/skills/api-reviewer/SKILL.md`
4. Validate against the checklist
5. Explain how to use it

### 3. Use Your Skill

Your skill is automatically available to any agent with `skill: true` enabled.

---

## Project Structure

```
skill-creator/
├── SKILL.md                      # Main entry point
├── README.md                     # This file
├── CHANGELOG.md                  # Version history
├── LICENSE                       # MIT License
│
├── references/                   # Reference docs
│   ├── skill-anatomy.md          # Structure breakdown
│   ├── frontmatter-spec.md       # YAML specification
│   └── validation-checklist.md   # Quality verification
│
├── templates/                    # Skill templates
│   └── minimal-skill.md          # Basic template with TODOs
│
└── workflows/                    # Step-by-step guides
    └── create-new-skill.md       # Complete creation workflow
```

---

## Skill Structure

### Minimal Example

```yaml
---
name: code-formatter
description: >-
  Formats code according to language-specific standards.
  Use when code needs formatting or style fixes.
  
  <example>
  User: "Format this Python code"
  Assistant: "I'll use the code-formatter skill."
  </example>

license: MIT
compatibility: agent-skills-standard
metadata:
  version: "1.0.0"
---

# Code Formatter

You are a code formatting specialist...
```

### Frontmatter Fields

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | Skill identifier (kebab-case) |
| `description` | Yes | What + when + examples (max 1024 chars) |
| `license` | No | MIT, Apache-2.0, BSD-3-Clause |
| `compatibility` | No | `agent-skills-standard`, `opencode`, `claude` |
| `metadata` | No | Version, author, category, tags |

See [`references/frontmatter-spec.md`](references/frontmatter-spec.md) for complete specification.

### Directory Structure

| Directory | Purpose | When to Use |
|-----------|---------|-------------|
| `references/` | Detailed documentation | Complex skills with multiple concepts |
| `templates/` | Reusable starting points | Skills that generate content |
| `workflows/` | Step-by-step guides | Multi-step processes |
| `examples/` | Complete examples | Show real usage patterns |

---

## Validation

### Quick Checklist

Use the [validation checklist](references/validation-checklist.md) to verify:

- [ ] Valid YAML frontmatter (no syntax errors)
- [ ] `name` is kebab-case and descriptive
- [ ] `description` has triggers and `<example>` blocks
- [ ] SKILL.md is under 500 lines
- [ ] English language throughout
- [ ] No executable code (pure markdown)
- [ ] README.md and LICENSE present

### Quality Scoring

Target score: **4.5+ / 5.0**

| Category | What it measures |
|----------|------------------|
| Frontmatter | Name, description quality, examples |
| Structure | Organization, file sizes, references |
| Instructions | Clarity, actionability, completeness |
| Examples | Concrete demonstrations, real scenarios |
| Documentation | README, LICENSE, CHANGELOG |

---

## Best Practices

### Do's

- **Write in English** - LLMs process English more efficiently
- **Use descriptive names** - `api-documenter` not `helper1`
- **Include examples** - Add `<example>` blocks in description
- **Keep SKILL.md focused** - Under 500 lines, use references/ for details
- **Document limitations** - Be explicit about what skill cannot do
- **Version your skill** - Use semantic versioning (1.0.0)

### Don'ts

| Anti-Pattern | Problem | Solution |
|--------------|---------|----------|
| Monolithic SKILL.md | Over 1000 lines | Split into references/ |
| Vague description | "Helps with tasks" | Specific triggers and examples |
| Missing examples | No `<example>` blocks | Add 1-2 usage examples |
| Executable code | Scripts in skill | Pure markdown only |
| Wrong language | Non-English content | Write in English |
| No versioning | Breaking changes unclear | Use CHANGELOG.md |

---

## Reference Documentation

| Document | Description |
|----------|-------------|
| [`skill-anatomy.md`](references/skill-anatomy.md) | Complete structure breakdown |
| [`frontmatter-spec.md`](references/frontmatter-spec.md) | YAML specification |
| [`validation-checklist.md`](references/validation-checklist.md) | Quality verification |

---

## Contributing

Contributions are welcome! Here's how:

### Adding Templates

1. Create a new template in `templates/`
2. Follow existing template structure
3. Include comprehensive documentation
4. Update this README

### Improving Documentation

1. Edit files in `references/` or `workflows/`
2. Test with real skills
3. Submit a pull request

### Reporting Issues

Open an issue with:
- Description of the problem
- Steps to reproduce
- Expected vs actual behavior

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

### Version 1.0.0 (Current)

**Initial Release:**
- SKILL.md with core functionality
- 3 reference documents (anatomy, frontmatter, validation)
- 1 template (minimal-skill.md)
- 1 workflow (create-new-skill.md)
- README, LICENSE, CHANGELOG

**Philosophy:**
Skills are **pure documentation** for LLM context, not executable software.

---

## License

MIT License - see [LICENSE](LICENSE) for details.

---

## Resources

- **Agent Skills Standard**: https://agentskills.io
- **Anthropic Skills**: https://github.com/anthropics/skills
- **OpenCode Documentation**: https://opencode.ai/docs/

---

## Philosophy

> "A great skill is like a well-written manual:
> - **Clear** about its purpose (description with examples)
> - **Focused** on one domain (single responsibility)
> - **Organized** for easy reference (SKILL.md + references)
> - **Portable** across platforms (Agent Skills standard)
> - **Documented** for contributors (README + LICENSE)"

Create skills that are **focused**, **clear**, and **reusable**.

---

<p align="center">
  Created by <strong>Rodrigo Lago</strong> for the Agent Skills community
</p>
