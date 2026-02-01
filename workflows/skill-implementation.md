# Skill Implementation

Phase 3 of skill creation: Create files and content.

---

## Step 3.1: Start with Template

**Option A: Copy from template**

```bash
# Read the minimal template
cat ~/.config/opencode/skills/skill-creator/templates/minimal-skill.md
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

---

## Step 3.2: Write the Frontmatter

Fill in required fields:

```yaml
---
name: your-skill-name # TODO: kebab-case, descriptive
description: >- # TODO: what + when + examples
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
license: MIT # Or Apache-2.0, BSD-3-Clause
compatibility: agent-skills-standard
metadata:
  category: development # or security, data-analysis, etc.
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

---

## Step 3.3: Write Core Instructions

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

Do NOT use this skill for:

- [Out of scope 1]
- [Out of scope 2]

## Examples

### Example 1: [Scenario]

**Input:**
[Example input]

**Output:**
[Example output]
```

**Guidelines:**

- Use **active voice** ("Analyze the code" not "The code should be analyzed")
- Include **specific examples** (concrete > abstract)
- Define **boundaries** (what skill won't do)
- Keep **SKILL.md < 500 lines** (use references/ for details)

---

## Step 3.4: Create References (if needed)

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

---

## Step 3.5: Create Templates (if needed)

**When to create templates:**

- Skill generates code/content
- Users need starting points
- Repetitive patterns exist

**Create template files:**

```bash
mkdir -p ~/.config/opencode/skills/your-skill-name/templates/
```

**Template structure:**

```markdown
# Template Name

Brief description of what this template is for.

## Usage

1. Copy this template
2. Replace {{VARIABLES}} with your values
3. Customize as needed

---

## Template Content

{{VARIABLE_1}}

# Your content here

{{VARIABLE_2}}

## Variables

| Variable         | Description | Example         |
| ---------------- | ----------- | --------------- |
| `{{VARIABLE_1}}` | What it is  | `example-value` |
```

**Use clear variable syntax:**

- `{{VARIABLE}}` or `$VARIABLE` or `[VARIABLE]`
- Be consistent within skill

---

## Step 3.6: Create Workflows (if needed)

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

### Step 1.2: [Step Name]

Instructions...

## Validation

- [ ] Checkpoint 1
- [ ] Checkpoint 2

## Troubleshooting

**Problem:** [Common issue]
**Solution:** [How to fix]
```

---

## Step 3.7: Add Examples (if needed)

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

[Input code/data/request]

## Process

1. [What happens step 1]
2. [What happens step 2]

## Output

[Expected output]

## Explanation

[Why this works, key concepts demonstrated]
```

---

## Step 3.8: Create README.md

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

\`\`\`bash
git clone https://github.com/username/skill-name.git ~/.config/opencode/skills/skill-name
\`\`\`

## Quick Start

[Simple example of using the skill]

## Documentation

- [SKILL.md](SKILL.md) - Main skill documentation
- [references/](references/) - Detailed references
- [templates/](templates/) - Ready-to-use templates

## Compatibility

This skill follows the [Agent Skills standard](https://agentskills.io).

**Compatible platforms:**

- OpenCode
- Claude / Claude Code
- Cursor
- VS Code

## License

MIT License - see [LICENSE](LICENSE) for details.

## Author

[Your Name]
```

---

## Step 3.9: Add LICENSE

**Recommended: MIT License**

```
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
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

## Step 3.10: Create CHANGELOG.md

```markdown
# Changelog

All notable changes to this skill will be documented in this file.

## [1.0.0] - 2026-01-25

### Added

- Initial release
- SKILL.md with core functionality
- README.md with installation guide
- LICENSE (MIT)
```

---

## Checklist: Implementation Complete?

- [ ] SKILL.md created with valid frontmatter
- [ ] Core instructions written
- [ ] References created (if needed)
- [ ] Templates created (if needed)
- [ ] Workflows created (if needed)
- [ ] Examples added (if needed)
- [ ] README.md created
- [ ] LICENSE added
- [ ] CHANGELOG.md created

---

## Next Step

→ Continue to [skill-validation-publishing.md](skill-validation-publishing.md) for Phases 4-6

---

_Back to [create-new-skill.md](create-new-skill.md) for overview_
