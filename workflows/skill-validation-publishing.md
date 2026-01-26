# Skill Validation & Publishing

Phases 4-6 of skill creation: Validate, Test, and Publish.

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

## Summary

**You've learned how to:**
- ✅ Validate skill against checklist
- ✅ Test with real scenarios
- ✅ Iterate based on feedback
- ✅ Publish to GitHub
- ✅ Share with community

**Quality Gates:**

| Gate | Criteria |
|------|----------|
| Validation | All checklist items pass |
| Testing | Real scenarios work correctly |
| Publishing | Repository complete with docs |

---

## Common Mistakes

1. **Vague description** → Add specific triggers and examples
2. **No examples** → Add at least one `<example>` block
3. **SKILL.md too long** → Split into references/
4. **Wrong name case** → Use kebab-case
5. **Missing license** → Add MIT or other open license
6. **Executable code** → Use pure markdown only
7. **Multiple languages** → Stick to English for LLM efficiency

---

## Resources

- **Agent Skills Standard**: https://agentskills.io
- **Validation Checklist**: [../references/validation-checklist.md](../references/validation-checklist.md)
- **Frontmatter Spec**: [../references/frontmatter-spec.md](../references/frontmatter-spec.md)
- **Minimal Template**: [../templates/minimal-skill.md](../templates/minimal-skill.md)

---

*Back to [create-new-skill.md](create-new-skill.md) for overview*
