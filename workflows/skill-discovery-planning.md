# Skill Discovery & Planning

Phases 1-2 of skill creation: Define purpose, scope, and structure.

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

| Level        | Structure                  | When to Use                             |
| ------------ | -------------------------- | --------------------------------------- |
| **Minimal**  | Just `SKILL.md`            | Simple, focused task (< 300 lines)      |
| **Standard** | `SKILL.md` + `references/` | Multiple concepts, needs organization   |
| **Complex**  | Full structure             | Multiple workflows, templates, examples |

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

**Your choice:** [ ] Minimal [ ] Standard [ ] Complex

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

## Checklist: Ready for Implementation?

Before moving to Phase 3, verify:

- [ ] Problem is clearly defined
- [ ] Scope boundaries are set (DO and DON'T)
- [ ] Skill name is kebab-case and descriptive
- [ ] Complexity level is chosen
- [ ] Required components are identified
- [ ] SKILL.md structure is planned

---

## Next Step

→ Continue to [skill-implementation.md](skill-implementation.md) for Phase 3

---

_Back to [create-new-skill.md](create-new-skill.md) for overview_
