# Agent Skill Creator

**Expert guidance for creating high-quality Agent Skills following the open standard.**

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/standard-Agent%20Skills-orange.svg)](https://agentskills.io)

---

## Overview

The **skill-creator** is a comprehensive skill that teaches AI agents how to create, structure, and refine Agent Skills that work across multiple platforms (OpenCode, Claude, Cursor, VS Code, GitHub Copilot, and 20+ others).

### What Are Agent Skills?

Agent Skills are **folders of markdown documentation** that AI agents can discover and use dynamically to improve their capabilities. Think of them as **plugins for AI agents** - reusable, portable, and version-controlled.

### Why This Skill?

- ✅ **Comprehensive templates** - Ready-to-use starting points with TODOs
- ✅ **Step-by-step workflows** - Guided creation process from start to finish
- ✅ **Validation checklists** - Ensure quality before publishing
- ✅ **Best practices** - Learn from established patterns
- ✅ **Standard-compliant** - Follows [Agent Skills open standard](https://agentskills.io)

---

## Features

### 📚 Complete Documentation

- **SKILL.md** - Main entry point with quick start guide
- **references/** - Deep dives into skill anatomy, frontmatter, and validation
- **templates/** - Minimal skill template ready to customize
- **workflows/** - Step-by-step skill creation process

### 🎯 What You'll Learn

1. **Skill Structure** - Required files, optional directories, organization patterns
2. **YAML Frontmatter** - Specification, required fields, optional metadata
3. **Content Organization** - Progressive disclosure, references, templates, workflows
4. **Validation** - Quality checklist, scoring rubric, automated checks
5. **Publishing** - GitHub setup, community sharing

### 🚀 Quick Capabilities

- Create minimal skills (single SKILL.md)
- Build complex skills (with references, templates, workflows)
- Validate existing skills against standard
- Refactor skills for better organization
- Ensure cross-platform compatibility

---

## Installation

### For OpenCode

```bash
# Clone to OpenCode skills directory
git clone https://github.com/rodrifmed/skill-creator.git ~/.config/opencode/skills/skill-creator
```

### For Claude Desktop / Claude Code

```bash
# Clone to Claude skills directory (adjust path as needed)
git clone https://github.com/rodrifmed/skill-creator.git ~/Library/Application\ Support/Claude/skills/skill-creator
```

### For Cursor / VS Code

```bash
# Clone to your project's skills directory
git clone https://github.com/rodrifmed/skill-creator.git .skills/skill-creator
```

### For Other Platforms

Consult your platform's documentation for the skills directory location, then:

```bash
git clone https://github.com/rodrifmed/skill-creator.git /path/to/skills/skill-creator
```

---

## Quick Start

### For AI Agents

When a user asks to create a skill, this skill provides:

1. **Templates** - Copy from `templates/minimal-skill.md`
2. **Workflow** - Follow `workflows/create-new-skill.md`
3. **Validation** - Check against `references/validation-checklist.md`

**Example usage:**
```
User: "Create a skill for analyzing Python code security"
Agent: Loads skill-creator → Uses template → Creates api-security-analyzer skill
```

### For Developers

1. **Read the main skill**: [SKILL.md](SKILL.md)
2. **Follow the workflow**: [workflows/create-new-skill.md](workflows/create-new-skill.md)
3. **Use the template**: [templates/minimal-skill.md](templates/minimal-skill.md)
4. **Validate your skill**: [references/validation-checklist.md](references/validation-checklist.md)

---

## Documentation Structure

```
skill-creator/
├── SKILL.md                           # 📖 Main entry point (~450 lines)
├── README.md                          # 📄 This file
├── LICENSE                            # ⚖️ MIT License
├── CHANGELOG.md                       # 📋 Version history
│
├── references/                        # 📚 Deep dive documentation
│   ├── skill-anatomy.md               # Structure breakdown
│   ├── frontmatter-spec.md            # YAML specification
│   └── validation-checklist.md        # Quality verification
│
├── templates/                         # 📝 Ready-to-use templates
│   └── minimal-skill.md               # Basic template with TODOs
│
└── workflows/                         # 🔄 Step-by-step guides
    └── create-new-skill.md            # Complete creation workflow
```

---

## Examples

### Creating a Minimal Skill

```yaml
---
name: code-formatter
description: >-
  Formats code according to language-specific standards.
  Use when code needs formatting, style fixes, or beautification.
  
  <example>
  User: "Format this Python code"
  Assistant: "I'll use the code-formatter skill."
  </example>
---

# Code Formatter

You are an expert code formatter...
```

### Creating a Complex Skill

See [workflows/create-new-skill.md](workflows/create-new-skill.md) for full guidance on creating skills with:
- Multiple reference files
- Templates for generated content
- Step-by-step workflows
- Complete examples

---

## Compatibility

This skill follows the **[Agent Skills open standard](https://agentskills.io)** and works across:

| Platform | Status | Notes |
|----------|--------|-------|
| OpenCode | ✅ Full support | Primary platform |
| Claude Desktop | ✅ Full support | Skills v1.0+ |
| Claude Code | ✅ Full support | Latest version |
| Cursor | ✅ Compatible | Agent Skills support |
| VS Code | ✅ Compatible | With extensions |
| GitHub Copilot | ✅ Compatible | Skills feature |
| Gemini CLI | ✅ Compatible | Standard support |
| Roo Code | ✅ Compatible | Standard support |
| Goose | ✅ Compatible | Standard support |

**Standard compliance:** Follows Agent Skills v1.0 specification

---

## Usage Examples

### Example 1: Create API Documentation Skill

```bash
User: "I need a skill to generate API documentation from code"

Agent process:
1. Loads skill-creator
2. Reads templates/minimal-skill.md
3. Customizes for API documentation use case
4. Creates ~/.config/opencode/skills/api-documenter/SKILL.md
5. Validates using validation-checklist.md
```

### Example 2: Validate Existing Skill

```bash
User: "Check if my security-audit skill follows best practices"

Agent process:
1. Loads skill-creator
2. Reads references/validation-checklist.md
3. Evaluates skill against checklist
4. Reports score and recommendations
```

### Example 3: Refactor Complex Skill

```bash
User: "My skill's SKILL.md is 800 lines, help organize it"

Agent process:
1. Loads skill-creator
2. Reviews references/skill-anatomy.md
3. Suggests splitting into references/
4. Helps create organized structure
```

---

## Philosophy

> **"A great skill is like a well-written manual:**
> - **Clear** about its purpose (description with examples)
> - **Focused** on one domain (single responsibility)
> - **Organized** for easy reference (SKILL.md + references)
> - **Portable** across platforms (Agent Skills standard)
> - **Documented** for contributors (README + LICENSE)"

### Core Principles

1. **Markdown-only** - No executable scripts (pure documentation)
2. **Progressive disclosure** - SKILL.md < 500 lines, details in references/
3. **English-first** - Optimal for LLM processing across platforms
4. **Standard-compliant** - Follows https://agentskills.io specification
5. **Template-based** - Provide copy-paste starting points with TODOs

---

## Contributing

Contributions are welcome! This skill is open source under the MIT License.

### How to Contribute

1. **Report Issues** - Found a problem? [Open an issue](https://github.com/rodrifmed/skill-creator/issues)
2. **Suggest Improvements** - Have ideas? Share them in [Discussions](https://github.com/rodrifmed/skill-creator/discussions)
3. **Submit Pull Requests** - Want to improve docs or add examples?
   - Fork the repository
   - Create a feature branch (`git checkout -b feature/amazing-improvement`)
   - Commit your changes (`git commit -m 'Add amazing improvement'`)
   - Push to the branch (`git push origin feature/amazing-improvement`)
   - Open a Pull Request

### What We're Looking For

- 📖 **Documentation improvements** - Clearer explanations, more examples
- 📝 **Additional templates** - More starting points for different skill types
- ✅ **Enhanced validation** - Better quality checks
- 🌍 **Translation** - While skills should be in English, README translations welcome
- 🐛 **Bug fixes** - Corrections and improvements

---

## Resources

### Official Documentation

- **Agent Skills Standard**: https://agentskills.io
- **Anthropic Skills Repo**: https://github.com/anthropics/skills
- **Agent Skills Spec**: https://github.com/agentskills/agentskills

### Related Skills

- **agent-creator** - Create OpenCode agents (companion to skill-creator)
- **prompt-engineering** - Improve prompt quality
- **code-review** - Review code systematically

### Community

- **OpenCode Community**: https://opencode.ai/community
- **Agent Skills Discord**: [Link when available]
- **GitHub Discussions**: Share your skills and get feedback

---

## FAQ

### Q: What's the difference between a skill and an agent?

**A:** 
- **Skills** = Knowledge/documentation for agents to use (folders in `~/.config/opencode/skills/`)
- **Agents** = Specialized AI personas with specific tools/permissions (files in `~/.config/opencode/agent/`)

Skills teach capabilities; agents apply them.

### Q: Can I create skills in languages other than English?

**A:** While you *can*, it's **not recommended**. English provides:
- Better LLM performance across platforms
- Lower token costs
- Wider compatibility
- Easier community collaboration

Write skills in English for optimal results.

### Q: How do I know if my skill is good quality?

**A:** Use the validation checklist: [references/validation-checklist.md](references/validation-checklist.md)

A quality skill scores 4-5/5 on:
- Valid YAML frontmatter
- Clear description with examples
- Actionable instructions
- Concrete examples
- Appropriate organization

### Q: Should I create one complex skill or multiple simple skills?

**A:** **Multiple simple skills** (Single Responsibility Principle)

✅ Good:
- `api-documenter` - Generates API docs
- `api-tester` - Tests API endpoints
- `api-security` - Audits API security

❌ Avoid:
- `api-helper` - Does everything (too broad)

### Q: Can I include executable code in skills?

**A:** **No.** Skills are pure markdown documentation. For tool integrations, create agents or use platform-specific features.

### Q: How do I version my skill?

**A:** Use semantic versioning (MAJOR.MINOR.PATCH) in:
1. `metadata.version` in frontmatter
2. CHANGELOG.md entries
3. Git tags (`git tag v1.0.0`)

---

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### What This Means

✅ You can:
- Use commercially
- Modify and distribute
- Use privately
- Sublicense

❌ You cannot:
- Hold liable
- Use trademark

**Attribution appreciated but not required.**

---

## Author

**Rodrigo Lago**

- GitHub: [@rodrifmed](https://github.com/rodrifmed)
- Skills created with ❤️ for the Agent Skills community

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

**Current version:** 1.0.0 (2026-01-25)

---

## Acknowledgments

- **Anthropic** - For creating the Agent Skills standard
- **OpenCode Team** - For building an amazing agent platform
- **Agent Skills Community** - For adoption and contributions
- **agent-creator** - Inspiration for structure and documentation style

---

## Star History

If you find this skill useful, consider starring the repository! ⭐

---

**Ready to create amazing skills?** Start with [SKILL.md](SKILL.md) or dive into [workflows/create-new-skill.md](workflows/create-new-skill.md)!

**Questions?** Open an [issue](https://github.com/rodrifmed/skill-creator/issues) or [discussion](https://github.com/rodrifmed/skill-creator/discussions).

**Happy skill creating! 🚀**
