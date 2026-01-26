# Minimal Skill Template

Basic Agent Skill template with TODO placeholders. Copy and customize this template to create your own skill.

---

```markdown
---
# TODO: Replace 'my-skill-name' with your skill's identifier (kebab-case)
name: my-skill-name

# TODO: Write description including:
# 1. What the skill does (1 sentence)
# 2. When to use it (triggers)
# 3. At least one <example> block
description: >-
  TODO: Describe what this skill does in one clear sentence.
  
  Use this skill when TODO: list triggers and use cases.
  
  <example>
  User: "TODO: Example user query"
  Assistant: "I'll use the my-skill-name skill to help with that."
  </example>

# TODO: Choose a license (MIT recommended)
license: MIT

# TODO: Set compatibility (agent-skills-standard recommended)
compatibility: agent-skills-standard

# TODO: Fill in metadata or remove if not needed
metadata:
  category: TODO  # development, documentation, security, testing, etc.
  version: "1.0.0"
  author: "TODO: Your Name"
  tags: [TODO, add, relevant, tags]
---

# TODO: Skill Display Name

TODO: Write 1-3 paragraphs introducing your skill.
- What does it do?
- Why is it useful?
- Who should use it?

## Core Principles

TODO: List the fundamental concepts or principles your skill is based on.

1. **Principle 1**: TODO: Explain first principle
2. **Principle 2**: TODO: Explain second principle
3. **Principle 3**: TODO: Explain third principle

## Quick Start

TODO: Provide the fastest way to use this skill.

**Example usage:**
```
TODO: Show a simple example
```

**What happens:**
1. TODO: Step 1
2. TODO: Step 2
3. TODO: Result

## Main Instructions

TODO: This is where you put the core instructions that agents will follow.

### When to Use This Skill

Use this skill when:
- TODO: Trigger condition 1
- TODO: Trigger condition 2
- TODO: Trigger condition 3

### What This Skill Does

This skill helps you:
1. **TODO: Capability 1** - Brief description
2. **TODO: Capability 2** - Brief description
3. **TODO: Capability 3** - Brief description

### How to Use This Skill

TODO: Provide step-by-step instructions or guidelines.

**Step 1: TODO**
TODO: Describe first step

**Step 2: TODO**
TODO: Describe second step

**Step 3: TODO**
TODO: Describe third step

## Operating Principles

TODO: Define how this skill should behave.

### Safety Guidelines

- **ALWAYS** TODO: What must always happen
- **NEVER** TODO: What must never happen
- **CHECK** TODO: What should be verified

### Quality Standards

- TODO: Quality criterion 1
- TODO: Quality criterion 2
- TODO: Quality criterion 3

## Common Tasks

TODO: List typical tasks this skill handles.

### Task 1: TODO

**Description:** TODO

**Steps:**
1. TODO
2. TODO
3. TODO

**Example:**
```
TODO: Show example
```

### Task 2: TODO

**Description:** TODO

**Steps:**
1. TODO
2. TODO
3. TODO

## Examples

TODO: Provide concrete, real-world examples.

### Example 1: TODO Scenario

**Situation:** TODO: Describe the situation

**Input:**
```
TODO: Show what user provides
```

**Process:**
TODO: Explain what the skill does

**Output:**
```
TODO: Show the result
```

### Example 2: TODO Scenario

TODO: Add another example

## Limitations

TODO: Be explicit about what this skill cannot do.

This skill:
- ❌ Cannot TODO: Limitation 1
- ❌ Cannot TODO: Limitation 2
- ❌ Cannot TODO: Limitation 3

## When NOT to Use

Avoid using this skill when:
- TODO: Situation 1
- TODO: Situation 2
- TODO: Situation 3

## Error Handling

TODO: Explain how to handle common errors.

| Error | Cause | Solution |
|-------|-------|----------|
| TODO | TODO | TODO |

## References

TODO: Link to detailed documentation (if using references/ directory)

For more details, see:
- [TODO: Reference Name](references/todo-reference.md)

## Best Practices

TODO: Share tips for getting the best results.

✅ **Do:**
- TODO: Best practice 1
- TODO: Best practice 2
- TODO: Best practice 3

❌ **Don't:**
- TODO: Anti-pattern 1
- TODO: Anti-pattern 2
- TODO: Anti-pattern 3

## Advanced Usage

TODO: For complex features (optional section)

### Advanced Feature 1

TODO: Describe advanced capability

### Advanced Feature 2

TODO: Describe another advanced capability

## Troubleshooting

TODO: Common issues and solutions.

**Problem:** TODO
**Solution:** TODO

**Problem:** TODO
**Solution:** TODO

## Version History

TODO: Track major changes (or use CHANGELOG.md)

- **1.0.0** - Initial release

## Contributing

TODO: How others can contribute (if open source)

Contributions welcome! Please:
1. Fork the repository
2. Make your changes
3. Submit a pull request

## License

TODO: Match with LICENSE file

This skill is released under the MIT License. See [LICENSE](LICENSE) for details.

## Additional Resources

TODO: Links to related documentation, tools, or skills.

- [TODO: Resource 1](https://example.com)
- [TODO: Resource 2](https://example.com)

---

**Remember:**
- Replace all TODO items
- Remove sections you don't need
- Add sections specific to your use case
- Keep SKILL.md under 500 lines (use references/ for details)
- Validate with [validation-checklist.md](../references/validation-checklist.md)
```

---

## Customization Checklist

Before using this template:

- [ ] Replace `my-skill-name` with actual skill identifier
- [ ] Write complete description with examples
- [ ] Fill in all frontmatter metadata
- [ ] Replace all TODO placeholders
- [ ] Add real examples and instructions
- [ ] Document limitations honestly
- [ ] Add license and author info
- [ ] Remove unused sections
- [ ] Validate with checklist

## Template Variables

If you want to use variable replacement:

| Variable | Replace With | Example |
|----------|--------------|---------|
| `{{SKILL_NAME}}` | Skill identifier | `code-reviewer` |
| `{{SKILL_DISPLAY_NAME}}` | Human name | `Code Reviewer` |
| `{{DESCRIPTION}}` | Full description | `Analyzes code...` |
| `{{AUTHOR}}` | Your name | `Jane Smith` |
| `{{CATEGORY}}` | Skill category | `development` |
| `{{LICENSE}}` | License type | `MIT` |

## Next Steps

After customizing this template:

1. **Save** as `~/.config/opencode/skills/your-skill-name/SKILL.md`
2. **Create** supporting files:
   - `README.md` - GitHub documentation
   - `LICENSE` - Full license text
   - `CHANGELOG.md` - Version history
3. **Add** optional directories:
   - `references/` - Detailed docs (if skill is complex)
   - `templates/` - Reusable templates (if skill generates content)
   - `workflows/` - Step-by-step guides (if multi-step processes)
4. **Validate** using [validation-checklist.md](../references/validation-checklist.md)
5. **Test** with real agent tasks
6. **Iterate** based on usage and feedback

## Tips

### Keep It Simple

Don't fill every section if not needed. A minimal viable skill only needs:
- Valid frontmatter (name + description)
- Clear instructions
- Usage examples

### Start Small, Grow Later

- Version 1.0: Basic functionality
- Version 1.1: Add references/
- Version 2.0: Add templates/ and workflows/

### Use References for Detail

If a topic needs >100 lines of explanation:
1. Create `references/topic-name.md`
2. Write detailed content there
3. Link from SKILL.md: `See [Topic](references/topic-name.md)`

### Test Early, Test Often

- Try using your skill with real tasks
- Ask others to try it
- Refine based on actual usage

## Common Customizations

### For Code Generation Skills

Add:
```markdown
## Output Format

Generated code follows:
- Style guide: TODO
- Formatting: TODO
- Comments: TODO

## Templates

See [templates/](templates/) for code templates.
```

### For Analysis Skills

Add:
```markdown
## Analysis Criteria

Checks for:
1. TODO: Criterion 1
2. TODO: Criterion 2

## Report Format

Analysis results include:
- Summary
- Detailed findings
- Recommendations
```

### For Automation Skills

Add:
```markdown
## Workflow Steps

1. **Prepare**: TODO
2. **Execute**: TODO
3. **Verify**: TODO
4. **Report**: TODO

## Prerequisites

Requires:
- TODO: Tool/dependency 1
- TODO: Tool/dependency 2
```

---

## Full Example (Completed)

See `agent-creator` skill for a complete, production-ready example:
- Location: `~/.config/opencode/skills/agent-creator/`
- Features all directories (references, templates, workflows)
- Well-documented and tested
- Can be used as reference

---

**Ready to create your skill?** Copy this template and start replacing TODOs!
