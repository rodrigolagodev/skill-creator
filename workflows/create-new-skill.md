# Creating a New Agent Skill

**Purpose:** Quick-start guide for creating Agent Skills following the open standard.

**Time Required:** 15-30 minutes for basic skill, 1-2 hours for complex skill

---

## Quick Start

For experienced users, here's the fast path:

```bash
# 1. Create skill directory
mkdir -p ~/.config/opencode/skills/your-skill-name

# 2. Create SKILL.md with this minimum structure:
```

```yaml
---
name: your-skill-name
description: >-
  What this skill does (1 sentence).
  When to use it (triggers).
  
  <example>
  User: "Example request"
  Assistant: "I'll use the your-skill-name skill."
  </example>
---

# Your Skill Name

[Your instructions here...]
```

```bash
# 3. Add README.md and LICENSE

# 4. Test in OpenCode
```

---

## Full Workflow Overview

This process has 6 phases:

| Phase | Description | Time | Guide |
|-------|-------------|------|-------|
| **1. Discovery** | Define purpose and scope | 5-10 min | [skill-discovery-planning.md](skill-discovery-planning.md) |
| **2. Planning** | Choose structure and components | 5-10 min | [skill-discovery-planning.md](skill-discovery-planning.md) |
| **3. Implementation** | Create files and content | 15-60 min | [skill-implementation.md](skill-implementation.md) |
| **4. Validation** | Verify quality and completeness | 5-10 min | [skill-validation-publishing.md](skill-validation-publishing.md) |
| **5. Testing** | Use skill in real scenarios | 10-20 min | [skill-validation-publishing.md](skill-validation-publishing.md) |
| **6. Publishing** | Share with community (optional) | 10-15 min | [skill-validation-publishing.md](skill-validation-publishing.md) |

---

## Phase Summaries

### Phase 1-2: Discovery & Planning

**Key Questions:**
1. What specific problem does this skill solve?
2. What should the skill DO and NOT do?
3. What structure do you need? (Minimal/Standard/Complex)

**Outputs:**
- Skill name (kebab-case)
- Scope definition
- Structure choice

→ [Detailed guide: skill-discovery-planning.md](skill-discovery-planning.md)

---

### Phase 3: Implementation

**Key Steps:**
1. Create SKILL.md with frontmatter
2. Write core instructions
3. Create references/ (if needed)
4. Create templates/ (if needed)
5. Create workflows/ (if needed)
6. Add README.md and LICENSE

**Structure:**
```
skill-name/
├── SKILL.md          # Entry point (< 500 lines)
├── README.md         # GitHub documentation
├── LICENSE           # MIT recommended
├── references/       # Detailed docs
├── templates/        # Starting points
└── workflows/        # Step-by-step guides
```

→ [Detailed guide: skill-implementation.md](skill-implementation.md)

---

### Phase 4-6: Validation, Testing & Publishing

**Validation Checklist:**
- [ ] Valid YAML frontmatter
- [ ] `name` is kebab-case
- [ ] `description` includes what/when/examples
- [ ] At least one `<example>` block
- [ ] Instructions are clear
- [ ] SKILL.md < 500 lines
- [ ] English language throughout

**Testing:**
1. Load skill in OpenCode
2. Test with real scenarios
3. Iterate based on results

**Publishing:**
1. Initialize git repository
2. Push to GitHub
3. Add topics: `agent-skills`, `opencode`, `claude`
4. Share with community

→ [Detailed guide: skill-validation-publishing.md](skill-validation-publishing.md)

---

## Quick Reference

### Command Cheatsheet

```bash
# Create structure
mkdir -p ~/.config/opencode/skills/skill-name/{references,templates,workflows}

# Verify
tree ~/.config/opencode/skills/skill-name/

# Count lines (should be < 500)
wc -l ~/.config/opencode/skills/skill-name/SKILL.md
```

### File Size Guidelines

| File | Recommended | Maximum |
|------|-------------|---------|
| SKILL.md | 200-400 lines | 500 lines |
| References | 300-500 lines | 1000 lines |
| Templates | 100-300 lines | 500 lines |
| Workflows | 200-400 lines | 800 lines |

### Common Mistakes

| Mistake | Fix |
|---------|-----|
| Vague description | Add specific triggers and examples |
| No examples | Add `<example>` blocks |
| SKILL.md too long | Split into references/ |
| Wrong name case | Use kebab-case |
| Missing license | Add MIT or similar |

---

## Resources

| Resource | Description |
|----------|-------------|
| [skill-discovery-planning.md](skill-discovery-planning.md) | Phases 1-2: Discovery and Planning |
| [skill-implementation.md](skill-implementation.md) | Phase 3: Implementation details |
| [skill-validation-publishing.md](skill-validation-publishing.md) | Phases 4-6: Validation, Testing, Publishing |
| [../references/validation-checklist.md](../references/validation-checklist.md) | Complete validation rubric |
| [../references/frontmatter-spec.md](../references/frontmatter-spec.md) | YAML specification |
| [../templates/minimal-skill.md](../templates/minimal-skill.md) | Basic template |

---

**Remember:** Great skills are focused, clear, and reusable. Start simple, add complexity only when needed.
