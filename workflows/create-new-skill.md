# Creating a New Agent Skill

**Purpose:** Step-by-step guide for creating high-quality Agent Skills that follow the open standard.

**Time Required:** 15-30 minutes for basic skill, 1-2 hours for complex skill

---

## Overview

This workflow guides you through creating a new skill from scratch. Follow these phases:

1. **Discovery** - Define purpose and scope
2. **Planning** - Choose structure and components
3. **Implementation** - Create files and content
4. **Validation** - Verify quality and completeness
5. **Testing** - Use skill in real scenarios
6. **Publishing** - Share with community (optional)

---

## Phase 1: Discovery

### Step 1.1: Define the Problem

**Ask yourself:**
- What specific problem does this skill solve?
- Who will use this skill (humans, agents, both)?
- What platforms should it work on (OpenCode, Claude, Cursor, all)?

**Example:**
```
Problem: Developers spend too much time writing API documentation
User: AI agents helping developers
Platform: OpenCode + Claude (Agent Skills standard)
```

### Step 1.2: Determine Skill Scope

**Questions:**
- What should the skill DO?
- What should the skill NOT do (boundaries)?
- What knowledge/resources does it need?

**Example:**
```
SHOULD DO:
- Generate API documentation from code
- Follow OpenAPI/Swagger standards
- Include examples and authentication details

SHOULD NOT DO:
- Generate actual API code (different skill)
- Test API endpoints (different skill)
- Deploy documentation (different skill)
```

**Rule:** One skill = One responsibility (Single Responsibility Principle)

### Step 1.3: Name Your Skill

Choose a **descriptive, kebab-case** name:

✅ **Good Names:**
- `api-documenter` (verb + object)
- `security-audit` (noun + noun)
- `code-reviewer` (noun + noun)
- `database-migration` (noun + noun)

❌ **Bad Names:**
- `helper`, `utils`, `tool` (too vague)
- `my-skill`, `skill-1` (not descriptive)
- `ApiDocumenter` (wrong case)

**Your skill name:** `_________________`

---

## Phase 2: Planning

### Step 2.1: Choose Complexity Level

Determine what structure you need:

| Level | Structure | When to Use |
|-------|-----------|-------------|
| **Minimal** | Just `SKILL.md` | Simple, focused task (< 300 lines) |
| **Standard** | `SKILL.md` + `references/` | Multiple concepts, needs organization |
| **Complex** | Full structure | Multiple workflows, templates, examples |

**Full Structure:**
```
skill-name/
├── SKILL.md                 # Entry point (< 500 lines)
├── README.md                # GitHub documentation
├── LICENSE                  # MIT recommended
├── CHANGELOG.md             # Version history
│
├── references/              # Detailed documentation
│   ├── concept-1.md
│   ├── concept-2.md
│   └── api-reference.md
│
├── templates/               # Ready-to-use templates
│   ├── basic-template.md
│   └── advanced-template.md
│
├── workflows/               # Step-by-step processes
│   └── common-workflow.md
│
└── examples/                # Complete examples
    └── example-1.md
```

**Your choice:** [ ] Minimal  [ ] Standard  [ ] Complex

### Step 2.2: Identify Required Components

**For your skill, which do you need?**

- [ ] **SKILL.md** (always required)
- [ ] **README.md** (recommended for GitHub)
- [ ] **LICENSE** (recommended for open source)
- [ ] **references/** - Do you have multiple complex concepts to explain?
- [ ] **templates/** - Will users need starting point files/code?
- [ ] **workflows/** - Are there multi-step processes to guide?
- [ ] **examples/** - Would complete examples help users?

### Step 2.3: Plan Your SKILL.md Structure

**Standard sections:**
```markdown
# Skill Name

Brief introduction (what is this skill?)

## Core Principles

High-level concepts (3-5 key ideas)

## Quick Start

How to use immediately (with examples)

## Main Instructions

Detailed guidance for the agent

## When to Use

Clear triggers and use cases

## References

Links to references/ files (if applicable)

## Examples

Concrete usage demonstrations
```

---

## Phase 3: Implementation

### Step 3.1: Start with Template

**Option A: Copy from template**
```bash
# Read the minimal template
cat ~/.config/opencode/skills/skill-creator/templates/minimal-skill.md

# Use it as starting point
```

**Option B: Create from scratch**

Use this basic structure:

```yaml
---
name: your-skill-name
description: >-
  [What it does - 1 sentence]
  [When to use - triggers and scenarios]
  
  <example>
  User: "[Example user request]"
  Assistant: "I'll use the [your-skill-name] skill."
  </example>
---

# Your Skill Name

[Your content here...]
```

### Step 3.2: Write the Frontmatter

Fill in required fields:

```yaml
---
name: your-skill-name              # TODO: kebab-case, descriptive
description: >-                    # TODO: what + when + examples
  What this skill does (be specific).
  When to use it (triggers).
  
  <example>
  User: "Example request"
  Assistant: "I'll use the skill-name skill."
  </example>
---
```

**Optional but recommended:**
```yaml
---
license: MIT                       # Or Apache-2.0, BSD-3-Clause
compatibility: agent-skills-standard
metadata:
  category: development            # or security, data-analysis, etc.
  version: "1.0.0"
  author: "Your Name"
  tags: [tag1, tag2]
---
```

**Validation:**
- [ ] `name` is kebab-case
- [ ] `description` has 3 parts: what/when/example
- [ ] At least one `<example>` block exists
- [ ] Description < 1024 characters

### Step 3.3: Write Core Instructions

**Structure your SKILL.md:**

```markdown
# Skill Name

[1-2 paragraph introduction]

## What This Skill Does

[Clear statement of purpose]

## Core Principles

1. **Principle 1** - Explanation
2. **Principle 2** - Explanation
3. **Principle 3** - Explanation

## Quick Start

**To use this skill:**

1. [Step 1]
2. [Step 2]
3. [Step 3]

## Main Instructions

### [Capability 1]

Instructions for this capability...

### [Capability 2]

Instructions for this capability...

## When to Use

Use this skill when:
- [Trigger scenario 1]
- [Trigger scenario 2]
- [Trigger scenario 3]

Do NOT use this skill for:
- [Out of scope 1]
- [Out of scope 2]

## Examples

### Example 1: [Scenario]

**Input:**
```
[Example input]
```

**Process:**
1. [Step 1]
2. [Step 2]

**Output:**
```
[Example output]
```
```

**Guidelines:**
- Use **active voice** ("Analyze the code" not "The code should be analyzed")
- Include **specific examples** (concrete > abstract)
- Define **boundaries** (what skill won't do)
- Keep **SKILL.md < 500 lines** (use references/ for details)

### Step 3.4: Create References (if needed)

**When to create references:**
- SKILL.md is getting > 400 lines
- You have distinct sub-topics
- Detailed specs/APIs need documentation

**Create reference files:**
```bash
mkdir -p ~/.config/opencode/skills/your-skill-name/references/
```

**Common reference patterns:**

```
references/
├── core-concepts.md        # Fundamental ideas
├── advanced-usage.md       # Complex scenarios
├── api-reference.md        # Technical specs
├── troubleshooting.md      # Common issues
└── best-practices.md       # Do's and don'ts
```

**Reference file structure:**
```markdown
# Topic Name

Brief introduction to this topic.

## Section 1

Content...

## Section 2

Content...

## Examples

Concrete examples...

## Related

- Link to other references
- Link to external resources
```

**Link from SKILL.md:**
```markdown
## Advanced Usage

For complex scenarios, see [references/advanced-usage.md](references/advanced-usage.md).
```

### Step 3.5: Create Templates (if needed)

**When to create templates:**
- Skill generates code/content
- Users need starting points
- Repetitive patterns exist

**Create template files:**
```bash
mkdir -p ~/.config/opencode/skills/your-skill-name/templates/
```

**Template best practices:**

```markdown
# Template Name

Brief description of what this template is for.

## Usage

1. Copy this template
2. Replace {{VARIABLES}} with your values
3. Customize as needed

---

## Template Content

```language
{{VARIABLE_1}}

# Your content here
{{VARIABLE_2}}

{{VARIABLE_3}}
```

## Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `{{VARIABLE_1}}` | What it is | `example-value` |
| `{{VARIABLE_2}}` | What it is | `example-value` |

## Customization Checklist

- [ ] Replace all {{VARIABLES}}
- [ ] Update [specific section]
- [ ] Verify [requirement]
```

**Use clear variable syntax:**
- `{{VARIABLE}}` or `$VARIABLE` or `[VARIABLE]`
- Be consistent within skill

### Step 3.6: Create Workflows (if needed)

**When to create workflows:**
- Multi-step processes
- Setup/configuration needed
- Common task sequences

**Create workflow files:**
```bash
mkdir -p ~/.config/opencode/skills/your-skill-name/workflows/
```

**Workflow structure:**
```markdown
# Workflow Name

**Purpose:** Brief description
**Time Required:** Estimated duration

---

## Overview

[What this workflow accomplishes]

## Prerequisites

- [ ] Requirement 1
- [ ] Requirement 2

## Phase 1: [Phase Name]

### Step 1.1: [Step Name]

Instructions...

**Example:**
```
Example output/code
```

### Step 1.2: [Step Name]

Instructions...

## Phase 2: [Phase Name]

[Continue pattern...]

## Validation

- [ ] Checkpoint 1
- [ ] Checkpoint 2

## Troubleshooting

**Problem:** [Common issue]
**Solution:** [How to fix]
```

### Step 3.7: Add Examples (if needed)

**Create example files:**
```bash
mkdir -p ~/.config/opencode/skills/your-skill-name/examples/
```

**Example file structure:**
```markdown
# Example: [Scenario Name]

Brief description of what this example demonstrates.

## Context

[Background/setup for this example]

## Input

```language
[Input code/data/request]
```

## Process

1. [What happens step 1]
2. [What happens step 2]
3. [What happens step 3]

## Output

```language
[Expected output]
```

## Explanation

[Why this works, key concepts demonstrated]

## Variations

- **Variation 1:** [How to modify for different case]
- **Variation 2:** [Alternative approach]
```

### Step 3.8: Create README.md (recommended)

**Purpose:** GitHub documentation for discovery

```markdown
# Skill Name

Brief tagline describing the skill.

## Overview

[2-3 paragraphs about what this skill does and why it's useful]

## Features

- Feature 1
- Feature 2
- Feature 3

## Installation

```bash
# Clone to OpenCode skills directory
git clone https://github.com/username/skill-name.git ~/.config/opencode/skills/skill-name

# Or for other platforms
git clone https://github.com/username/skill-name.git /path/to/skills/skill-name
```

## Quick Start

[Simple example of using the skill]

## Documentation

- [SKILL.md](SKILL.md) - Main skill documentation
- [references/](references/) - Detailed references
- [templates/](templates/) - Ready-to-use templates
- [workflows/](workflows/) - Step-by-step guides

## Compatibility

This skill follows the [Agent Skills standard](https://agentskills.io).

**Compatible platforms:**
- OpenCode
- Claude / Claude Code
- Cursor
- VS Code
- [Other platforms]

## Examples

[Link to examples/ or show quick example]

## Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## License

MIT License - see [LICENSE](LICENSE) for details.

## Author

[Your Name] - [Contact/Links]

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.
```

### Step 3.9: Add LICENSE

**Recommended: MIT License**

```bash
# Create LICENSE file
cat > ~/.config/opencode/skills/your-skill-name/LICENSE << 'EOF'
MIT License

Copyright (c) 2026 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
EOF
```

**Other license options:**
- Apache-2.0 (more permissive with patent grants)
- BSD-3-Clause (permissive with attribution)
- CC-BY-4.0 (Creative Commons for documentation)

### Step 3.10: Create CHANGELOG.md

**Track version history:**

```markdown
# Changelog

All notable changes to this skill will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- [Future features]

## [1.0.0] - 2026-01-25

### Added
- Initial release
- SKILL.md with core functionality
- [List major components]
- [List key features]

### Documentation
- README.md with installation guide
- LICENSE (MIT)
- [Other docs]

[Unreleased]: https://github.com/username/skill-name/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/username/skill-name/releases/tag/v1.0.0
```

---

## Phase 4: Validation

### Step 4.1: Run Validation Checklist

Use the complete checklist: [../references/validation-checklist.md](../references/validation-checklist.md)

**Quick validation:**

```bash
cd ~/.config/opencode/skills/your-skill-name/

# Check file exists
test -f SKILL.md && echo "✓ SKILL.md exists" || echo "✗ SKILL.md missing"

# Check frontmatter
head -n 10 SKILL.md | grep "^name:" && echo "✓ Has name field" || echo "✗ Missing name"
head -n 15 SKILL.md | grep "^description:" && echo "✓ Has description" || echo "✗ Missing description"

# Check for examples
grep "<example>" SKILL.md && echo "✓ Has examples" || echo "✗ Missing examples"

# Count lines (should be < 500)
LINES=$(wc -l < SKILL.md)
[ $LINES -lt 500 ] && echo "✓ SKILL.md is $LINES lines (< 500)" || echo "⚠ SKILL.md is $LINES lines (> 500)"
```

**Manual checks:**
- [ ] YAML frontmatter is valid (no syntax errors)
- [ ] `name` is kebab-case
- [ ] `description` includes what/when/examples
- [ ] At least one `<example>` block
- [ ] Instructions are clear and actionable
- [ ] Examples are concrete and realistic
- [ ] No executable code (pure markdown)
- [ ] English language throughout
- [ ] README.md exists
- [ ] LICENSE exists

### Step 4.2: Verify File Structure

```bash
# Expected minimal structure
tree ~/.config/opencode/skills/your-skill-name/

# Should see at minimum:
# .
# ├── SKILL.md
# ├── README.md (recommended)
# └── LICENSE (recommended)
```

### Step 4.3: Test YAML Parsing

**If you have `yq` installed:**
```bash
# Extract and validate frontmatter
sed -n '/^---$/,/^---$/p' SKILL.md | yq eval '.'
```

**Manual test:**
- Copy frontmatter (between `---` markers)
- Paste into https://www.yamllint.com/
- Check for errors

---

## Phase 5: Testing

### Step 5.1: Load Skill in OpenCode

```bash
# Verify skill location
ls -la ~/.config/opencode/skills/your-skill-name/

# Restart OpenCode or reload skills
# (Platform-specific)
```

### Step 5.2: Test with Real Scenario

**Create a test scenario:**

1. **Identify a task** the skill should handle
2. **Request it** as if you're a user
3. **Observe** if agent loads the skill
4. **Verify** output quality

**Example test:**
```
Test Skill: api-documenter
Scenario: "Document this API endpoint"
Input: [code snippet]
Expected: Agent loads api-documenter, generates OpenAPI docs
Actual: [What happened?]
Result: [ ] Pass  [ ] Fail
```

### Step 5.3: Iterate Based on Testing

**Common issues and fixes:**

| Issue | Likely Cause | Fix |
|-------|--------------|-----|
| Skill not loading | YAML syntax error | Validate frontmatter |
| Agent doesn't activate | Description too vague | Add specific triggers/examples |
| Output quality poor | Instructions unclear | Add more examples, detail |
| Wrong skill activates | Overlapping descriptions | Refine scope, add boundaries |

**Refinement process:**
1. Test skill with realistic task
2. Identify gaps/issues
3. Update SKILL.md
4. Test again
5. Repeat until quality is high

---

## Phase 6: Publishing (Optional)

### Step 6.1: Prepare for GitHub

**Initialize git repository:**
```bash
cd ~/.config/opencode/skills/your-skill-name/
git init
git add .
git commit -m "Initial commit: v1.0.0"
```

**Create .gitignore (if needed):**
```bash
cat > .gitignore << 'EOF'
# OS files
.DS_Store
Thumbs.db

# Editor files
.vscode/
.idea/

# Temporary files
*.tmp
*.bak
*~
EOF
```

### Step 6.2: Create GitHub Repository

1. Go to https://github.com/new
2. Name: `skill-name` (match your folder name)
3. Description: Copy from your `description` field
4. Public/Private: Your choice
5. Don't initialize with README (you already have one)
6. Create repository

### Step 6.3: Push to GitHub

```bash
git remote add origin https://github.com/username/skill-name.git
git branch -M main
git push -u origin main
```

### Step 6.4: Add Topics/Tags

On GitHub repository page:
- Click "About" settings (⚙️)
- Add topics: `agent-skills`, `opencode`, `claude`, `ai-agents`, etc.
- Add website: `https://agentskills.io`

### Step 6.5: Share with Community

**Where to share:**
- [Agent Skills Registry](https://agentskills.io) (if available)
- OpenCode community
- GitHub discussions
- Social media (X/Twitter, LinkedIn, etc.)

**Announcement template:**
```
🚀 Just released [Skill Name] - an Agent Skill for [purpose]

✨ Features:
- Feature 1
- Feature 2
- Feature 3

Compatible with OpenCode, Claude, Cursor, and more platforms.

📦 https://github.com/username/skill-name

#AgentSkills #AI #OpenCode
```

---

## Appendix: Quick Reference

### Command Cheatsheet

```bash
# Create skill directory
mkdir -p ~/.config/opencode/skills/skill-name/{references,templates,workflows,examples}

# Create SKILL.md
touch ~/.config/opencode/skills/skill-name/SKILL.md

# Verify structure
tree ~/.config/opencode/skills/skill-name/

# Count lines
wc -l ~/.config/opencode/skills/skill-name/SKILL.md

# Validate YAML
sed -n '/^---$/,/^---$/p' ~/.config/opencode/skills/skill-name/SKILL.md | yq eval '.'

# Search for examples
grep -n "<example>" ~/.config/opencode/skills/skill-name/SKILL.md
```

### File Size Guidelines

| File | Recommended Size | Maximum |
|------|------------------|---------|
| SKILL.md | 200-400 lines | 500 lines |
| Reference files | 300-500 lines | 1000 lines |
| Templates | 100-300 lines | 500 lines |
| Workflows | 200-400 lines | 800 lines |
| Examples | 50-150 lines | 300 lines |
| README.md | 100-200 lines | 400 lines |

### Common Mistakes

1. **Vague description** → Add specific triggers and examples
2. **No examples** → Add at least one `<example>` block
3. **SKILL.md too long** → Split into references/
4. **Wrong name case** → Use kebab-case
5. **Missing license** → Add MIT or other open license
6. **Executable code** → Use pure markdown only
7. **Multiple languages** → Stick to English for LLM efficiency

### Resources

- **Agent Skills Standard**: https://agentskills.io
- **Validation Checklist**: [../references/validation-checklist.md](../references/validation-checklist.md)
- **Frontmatter Spec**: [../references/frontmatter-spec.md](../references/frontmatter-spec.md)
- **Skill Anatomy**: [../references/skill-anatomy.md](../references/skill-anatomy.md)
- **Minimal Template**: [../templates/minimal-skill.md](../templates/minimal-skill.md)

---

## Summary

**You've learned how to:**
- ✅ Define skill purpose and scope
- ✅ Plan skill structure
- ✅ Write valid frontmatter
- ✅ Create clear instructions
- ✅ Organize with references/templates/workflows
- ✅ Validate against checklist
- ✅ Test with real scenarios
- ✅ Publish to GitHub

**Next steps:**
1. Start with a simple skill (minimal structure)
2. Test thoroughly
3. Share with community
4. Iterate based on feedback

**Remember:** Great skills are focused, clear, and reusable. Start simple, add complexity only when needed.

---

**Happy skill creating! 🚀**
