# Frontmatter Specification

Complete YAML frontmatter specification for Agent Skills.

## Overview

Agent Skills use **YAML frontmatter** at the beginning of `SKILL.md` to provide metadata that agents and platforms use for discovery and activation.

```yaml
---
# Required fields
name: skill-identifier
description: What it does and when to use it

# Optional fields
license: MIT
compatibility: agent-skills-standard
metadata:
  category: development
  version: "1.0.0"
  author: "Your Name"
---
```

---

## Required Fields

### `name`

**Type:** String  
**Format:** kebab-case (lowercase, hyphens only)  
**Max length:** 64 characters  
**Required:** ✅ Yes

**Purpose:** Unique identifier for the skill.

**Valid examples:**

```yaml
name: code-reviewer
name: api-documentation
name: database-migration-helper
name: security-audit
```

**Invalid examples:**

```yaml
name: Code Reviewer      # ❌ Contains spaces
name: api_documentation  # ❌ Uses underscores
name: mySkill            # ❌ CamelCase
name: my skill           # ❌ Spaces
```

**Rules:**

- Must be unique within your skills directory
- Use nouns or verb phrases
- Descriptive, not generic (`code-reviewer` not `helper`)
- Match folder name: `~/.config/opencode/skills/code-reviewer/`

---

### `description`

**Type:** String (multi-line with `>-` or `|`)  
**Max length:** 1024 characters  
**Required:** ✅ Yes

**Purpose:** Tells agents **what** the skill does and **when** to use it.

**Structure:**

```yaml
description: >-
  [WHAT] One sentence describing the skill.
  [WHEN] When to use it (triggers).

  <example>
  User: "[trigger phrase]"
  Assistant: "I'll use the [skill-name] skill."
  </example>
```

**Example 1: Code Review Skill**

```yaml
description: >-
  Analyzes code for quality, security, and best practices using static analysis.
  Use when reviewing pull requests, auditing codebases, or checking for vulnerabilities.

  <example>
  User: "Review this Python code for security issues"
  Assistant: "I'll use the code-reviewer skill to analyze security."
  </example>

  <example>
  User: "Check if this follows best practices"
  Assistant: "I'll use the code-reviewer skill."
  </example>
```

**Example 2: Documentation Skill**

```yaml
description: >-
  Creates comprehensive documentation for APIs, libraries, and codebases.
  Use when documenting new features, generating API references, or creating guides.

  <example>
  User: "Document this API endpoint"
  Assistant: "I'll use the api-documentation skill."
  </example>
```

**Best Practices:**

- ✅ Start with what it does (1 sentence)
- ✅ Include when to use (triggers)
- ✅ Add 1-2 `<example>` blocks
- ✅ Write in third person
- ✅ Be specific, not vague
- ❌ Don't exceed 1024 chars
- ❌ Don't omit examples
- ❌ Don't be too generic ("helps with coding")

**Example Blocks:**

Agents use `<example>` blocks to learn **when** to activate the skill.

```yaml
<example>
User: "exact or similar phrase"
Assistant: "I'll use the [skill-name] skill."
</example>
```

Multiple examples improve activation accuracy:

```yaml
<example>
User: "Review this code"
Assistant: "I'll use the code-reviewer skill."
</example>

<example>
User: "Check for security issues"
Assistant: "I'll use the code-reviewer skill for security analysis."
</example>
```

---

## Optional Fields

### `license`

**Type:** String  
**Common values:** `MIT`, `Apache-2.0`, `BSD-3-Clause`, `GPL-3.0`  
**Required:** ⚠️ Recommended

**Purpose:** Specifies the skill's license for redistribution.

```yaml
license: MIT
```

**Recommended licenses:**
| License | Use Case |
|---------|----------|
| `MIT` | Maximum freedom, minimal restrictions |
| `Apache-2.0` | Patent protection, commercial-friendly |
| `BSD-3-Clause` | Similar to MIT with attribution requirement |

**Must match LICENSE file** in skill root:

```
skill-name/
├── SKILL.md
└── LICENSE    # Full license text
```

---

### `compatibility`

**Type:** String or Array  
**Common values:** `agent-skills-standard`, `opencode`, `claude`, `cursor`  
**Required:** ⚠️ Recommended

**Purpose:** Indicates platform compatibility.

**Single platform:**

```yaml
compatibility: opencode
```

**Multiple platforms:**

```yaml
compatibility:
  - agent-skills-standard
  - opencode
  - claude
  - cursor
```

**Standard compliance:**

```yaml
compatibility: agent-skills-standard
```

Use `agent-skills-standard` when following the open standard (recommended).

---

### `metadata`

**Type:** Object (nested YAML)  
**Required:** ❌ Optional

**Purpose:** Additional organizational metadata.

```yaml
metadata:
  category: development
  version: "1.0.0"
  author: "Your Name"
  tags: [python, testing, security]
  repository: "https://github.com/user/repo"
  homepage: "https://example.com"
  created: "2026-01-20"
  updated: "2026-01-25"
```

#### `metadata.category`

Organizational category for grouping skills.

**Common categories:**

```yaml
metadata:
  category: development       # Code-related
  category: documentation     # Docs creation
  category: security          # Security analysis
  category: testing           # Testing automation
  category: data-science      # Data analysis
  category: devops            # Infrastructure
  category: ai                # AI/ML tasks
  category: automation        # General automation
```

#### `metadata.version`

Semantic versioning for the skill.

```yaml
metadata:
  version: "1.0.0" # Major.Minor.Patch
```

**Format:** [Semantic Versioning](https://semver.org/)

- `1.0.0` - Initial release
- `1.1.0` - Added features (backward compatible)
- `2.0.0` - Breaking changes

**Update CHANGELOG.md** when bumping version.

#### `metadata.author`

Skill creator identification.

```yaml
metadata:
  author: "Your Name"
  # or
  author: "Your Name <email@example.com>"
  # or
  author:
    name: "Your Name"
    email: "email@example.com"
    url: "https://yoursite.com"
```

#### `metadata.tags`

Keywords for discovery and search.

```yaml
metadata:
  tags: [python, security, static-analysis, linting]
```

**Best practices:**

- 3-7 tags
- Lowercase
- Technology names (python, javascript)
- Use cases (security, testing)
- Techniques (static-analysis, automation)

#### `metadata.repository`

Link to source code repository.

```yaml
metadata:
  repository: "https://github.com/username/skill-name"
```

#### `metadata.homepage`

Skill documentation website.

```yaml
metadata:
  homepage: "https://skill-name.dev"
```

#### `metadata.created` / `metadata.updated`

Timestamps for tracking.

```yaml
metadata:
  created: "2026-01-20"
  updated: "2026-01-25"
```

**Format:** ISO 8601 date (`YYYY-MM-DD`)

---

## Complete Example

```yaml
---
# Required
name: security-auditor
description: >-
  Performs comprehensive security audits on codebases to identify vulnerabilities,
  misconfigurations, and potential attack vectors. Uses static analysis, dependency
  checking, and security best practice validation.

  Use when reviewing code for security issues, auditing projects before deployment,
  or investigating potential security concerns.

  <example>
  User: "Audit this codebase for security vulnerabilities"
  Assistant: "I'll use the security-auditor skill to perform a comprehensive scan."
  </example>

  <example>
  User: "Check for SQL injection risks"
  Assistant: "I'll use the security-auditor skill focusing on injection vulnerabilities."
  </example>

# Optional
license: MIT
compatibility: agent-skills-standard

metadata:
  category: security
  version: "2.1.0"
  author: "Security Team <security@example.com>"
  tags: [security, audit, static-analysis, vulnerabilities]
  repository: "https://github.com/example/security-auditor"
  homepage: "https://security-auditor.dev"
  created: "2025-06-15"
  updated: "2026-01-25"
---
```

---

## Validation Rules

### Syntax Validation

**Valid YAML:**

```yaml
---
name: my-skill
description: This is valid
---
```

**Invalid YAML:**

```yaml
---
name my-skill          # ❌ Missing colon
description: "unclosed # ❌ Unclosed quote
---
```

**Multi-line strings:**

Use `>-` for folded (removes newlines):

```yaml
description: >-
  Line 1
  Line 2
  Line 3

# Becomes: "Line 1 Line 2 Line 3"
```

Use `|` for literal (keeps newlines):

```yaml
description: |
  Line 1
  Line 2
  Line 3

# Becomes: "Line 1\nLine 2\nLine 3"
```

### Field Validation

| Field         | Rule         | Invalid Example                                                      | Valid Example          |
| ------------- | ------------ | -------------------------------------------------------------------- | ---------------------- |
| `name`        | kebab-case   | `My Skill`                                                           | `my-skill`             |
| `name`        | < 64 chars   | `very-long-skill-name-that-exceeds-the-maximum-allowed-length-limit` | `concise-skill`        |
| `description` | < 1024 chars | (1500 char description)                                              | (500 char description) |
| `description` | Has examples | No `<example>`                                                       | Has `<example>` blocks |
| `license`     | Valid SPDX   | `My License`                                                         | `MIT`                  |
| `version`     | Semver       | `1.0`                                                                | `1.0.0`                |

---

## Common Mistakes

### 1. Missing Required Fields

❌ **Wrong:**

```yaml
---
name: my-skill
# Missing description
---
```

✅ **Correct:**

```yaml
---
name: my-skill
description: >-
  What it does.

  <example>
  User: "..."
  Assistant: "I'll use my-skill"
  </example>
---
```

### 2. Invalid name Format

❌ **Wrong:**

```yaml
name: My Skill        # Spaces
name: my_skill        # Underscores
name: mySkill         # CamelCase
```

✅ **Correct:**

```yaml
name: my-skill # kebab-case
```

### 3. No Examples in Description

❌ **Wrong:**

```yaml
description: This skill helps with coding tasks.
```

✅ **Correct:**

```yaml
description: >-
  This skill helps with coding tasks.

  <example>
  User: "Help me code this feature"
  Assistant: "I'll use this skill."
  </example>
```

### 4. Description Too Long

❌ **Wrong:**

```yaml
description: >-
  [1500 characters of text...]
  # Exceeds 1024 character limit
```

✅ **Correct:**

```yaml
description: >-
  Concise description (< 1024 chars).
  Move details to SKILL.md body.

  <example>...</example>
```

### 5. Incorrect Metadata Nesting

❌ **Wrong:**

```yaml
category: development # Not nested under metadata
version: "1.0.0"
```

✅ **Correct:**

```yaml
metadata:
  category: development
  version: "1.0.0"
```

---

## Testing Your Frontmatter

### Manual Validation

1. **YAML syntax:**

   ```bash
   # Using Python
   python -c "import yaml; yaml.safe_load(open('SKILL.md').read().split('---')[1])"
   ```

2. **Field presence:**
   - [ ] Has `name`
   - [ ] Has `description`
   - [ ] Description has `<example>` blocks
   - [ ] All fields valid types

3. **Length limits:**
   - [ ] `name` < 64 chars
   - [ ] `description` < 1024 chars

### Checklist

Use [validation-checklist.md](validation-checklist.md) for complete validation.

---

## References

- **YAML Specification**: https://yaml.org/spec/
- **Semantic Versioning**: https://semver.org/
- **SPDX License List**: https://spdx.org/licenses/
- **Agent Skills Spec**: https://agentskills.io
