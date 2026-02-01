# Validation Checklist

Complete field-by-field validation checklist for Agent Skills.

## Overview

Use this checklist to ensure your skill follows the Agent Skills standard and best practices. Target: **All items checked** before publishing.

---

## Quick Validation

### Critical Requirements (Must Pass)

- [ ] **SKILL.md exists** in skill root directory
- [ ] **Valid YAML frontmatter** (no syntax errors)
- [ ] **name field present** and valid (kebab-case, < 64 chars)
- [ ] **description field present** and valid (< 1024 chars)
- [ ] **description contains examples** (at least one `<example>` block)
- [ ] **Content in English** (LLM efficiency)
- [ ] **No executable scripts** (pure markdown)

If any critical requirement fails, **stop and fix** before continuing.

---

## Detailed Validation

### 1. File Structure

#### Required Files

- [ ] `SKILL.md` exists in root
- [ ] `SKILL.md` is valid markdown
- [ ] `SKILL.md` has YAML frontmatter (between `---` markers)

#### Recommended Files

- [ ] `README.md` present (for GitHub)
- [ ] `LICENSE` file present (MIT/Apache recommended)
- [ ] `CHANGELOG.md` present (version history)

#### Optional Directories

- [ ] `references/` used if SKILL.md > 650 lines
- [ ] `templates/` included if skill generates content
- [ ] `workflows/` included if multi-step processes exist
- [ ] `examples/` included if concrete examples helpful

#### File Naming

- [ ] Skill folder name matches `name` in frontmatter
- [ ] All files use kebab-case or camelCase consistently
- [ ] No spaces in file/folder names

---

### 2. Frontmatter Validation

#### Required Fields

**name:**

- [ ] `name` field exists
- [ ] kebab-case format (lowercase, hyphens only)
- [ ] No spaces, underscores, or special characters
- [ ] Descriptive (not `helper`, `util`, `skill1`)
- [ ] Unique within skills directory
- [ ] Length < 64 characters
- [ ] Matches skill folder name

**description:**

- [ ] `description` field exists
- [ ] Length < 1024 characters
- [ ] Includes **WHAT** the skill does (first sentence)
- [ ] Includes **WHEN** to use it (triggers)
- [ ] Contains at least 1 `<example>` block
- [ ] Example shows user query and agent response
- [ ] Written in third person
- [ ] Clear and specific (not vague)

#### Optional Fields

**license:**

- [ ] If present, valid SPDX identifier (MIT, Apache-2.0, etc.)
- [ ] Matches LICENSE file in root (if exists)

**compatibility:**

- [ ] If present, valid value (agent-skills-standard, opencode, claude, etc.)
- [ ] Accurately reflects platform support

**metadata:**

- [ ] If present, properly nested under `metadata:` key
- [ ] All metadata fields valid types

**metadata.category:**

- [ ] If present, single category (not array)
- [ ] Descriptive category name

**metadata.version:**

- [ ] If present, follows semantic versioning (1.0.0)
- [ ] Matches version in CHANGELOG.md

**metadata.author:**

- [ ] If present, includes name
- [ ] Optionally includes email/URL

**metadata.tags:**

- [ ] If present, array of lowercase strings
- [ ] 3-7 tags (not too few, not too many)
- [ ] Relevant to skill purpose

**metadata.repository:**

- [ ] If present, valid GitHub/GitLab URL

---

### 3. SKILL.md Content

#### Structure

- [ ] Has main title (H1: `#`)
- [ ] Has logical sections (H2: `##`)
- [ ] Uses standard markdown headings (not XML tags)
- [ ] No more than 3 heading levels deep (H1, H2, H3)

#### Length

- [ ] SKILL.md < 650 lines (ideal)
- [ ] If > 650 lines, content split into references/
- [ ] If > 1000 lines, **must** refactor

#### Content Quality

- [ ] Clear introduction (what skill does)
- [ ] Core principles or concepts explained
- [ ] Instructions are actionable
- [ ] Examples demonstrate real usage
- [ ] References linked (if applicable)
- [ ] No broken links
- [ ] Code blocks have language tags (`python, `yaml)

#### Language

- [ ] Entire skill in English
- [ ] Clear, concise writing
- [ ] No spelling errors
- [ ] Consistent terminology

#### Completeness

- [ ] Explains **what** skill does
- [ ] Explains **when** to use it
- [ ] Explains **how** to use it
- [ ] Documents limitations (what it cannot do)
- [ ] Includes usage examples

---

### 4. README.md (if present)

- [ ] Has skill name as title
- [ ] Brief overview (1-2 paragraphs)
- [ ] Installation instructions
- [ ] Quick start example
- [ ] Link to SKILL.md for full docs
- [ ] License information
- [ ] Contact/contribution info (optional)
- [ ] Badges (optional but recommended)

---

### 5. references/ Directory (if present)

#### Organization

- [ ] Each file focused on one topic
- [ ] Files use kebab-case naming
- [ ] Clear, descriptive filenames
- [ ] No redundant content between files

#### Content

- [ ] Each reference < 600 lines (ideal < 300)
- [ ] Proper markdown structure
- [ ] Linked from SKILL.md
- [ ] Examples included

#### Common References

- [ ] Concepts explained in detail
- [ ] API/technical specs documented
- [ ] Anti-patterns documented (what to avoid)
- [ ] Troubleshooting guide (if complex)

---

### 6. templates/ Directory (if present)

#### Organization

- [ ] At least 1 template provided
- [ ] Templates use clear naming
- [ ] Templates include TODOs or placeholders

#### Content

- [ ] Variables marked clearly (`{{VAR}}` or `$VAR` or `TODO`)
- [ ] Each template < 400 lines
- [ ] Comments explain usage
- [ ] Examples of filled templates (optional)

#### Usability

- [ ] Templates are copy-paste ready
- [ ] Clear what needs customization
- [ ] Documented in SKILL.md

---

### 7. workflows/ Directory (if present)

#### Organization

- [ ] Each workflow in separate file
- [ ] Clear, descriptive filenames
- [ ] Logical ordering of steps

#### Content

- [ ] Overview section (what workflow does)
- [ ] Prerequisites listed
- [ ] Steps numbered and clear
- [ ] Expected outputs documented
- [ ] Troubleshooting section (for complex workflows)
- [ ] Each workflow < 800 lines

#### Usability

- [ ] Can follow step-by-step without confusion
- [ ] Commands are copy-pasteable
- [ ] Verification steps included

---

### 8. examples/ Directory (if present)

- [ ] At least 1 complete example
- [ ] Each example has README.md
- [ ] Examples demonstrate real use cases
- [ ] Examples work as documented
- [ ] Examples well-organized in subdirectories

---

### 9. Quality Checks

#### Documentation

- [ ] All markdown files valid
- [ ] No broken internal links
- [ ] No broken external links (or marked as such)
- [ ] Code blocks properly formatted
- [ ] Tables properly formatted

#### Consistency

- [ ] Consistent terminology throughout
- [ ] Consistent formatting style
- [ ] Consistent heading capitalization
- [ ] Consistent code style in examples

#### Completeness

- [ ] No TODO comments left unresolved
- [ ] No placeholder text left in
- [ ] All examples complete
- [ ] All workflows tested

---

### 10. Best Practices

#### Agent Activation

- [ ] Description has clear triggers
- [ ] Examples show when to use skill
- [ ] Skill purpose is unambiguous

#### Maintainability

- [ ] Version number current (if versioned)
- [ ] CHANGELOG.md updated (if versioned)
- [ ] Last updated date accurate (if tracked)
- [ ] Contact info current

#### Discoverability

- [ ] README.md makes purpose clear
- [ ] Tags relevant (if used)
- [ ] Category appropriate (if used)
- [ ] Repository link present (if public)

---

## Scoring Rubric

Rate each category 0-5:

| Category          | Score  | Description                     |
| ----------------- | ------ | ------------------------------- |
| **Structure**     | \_\_/5 | Files organized, naming correct |
| **Frontmatter**   | \_\_/5 | Valid, complete, well-written   |
| **Content**       | \_\_/5 | Clear, actionable, complete     |
| **Documentation** | \_\_/5 | README, examples, references    |
| **Quality**       | \_\_/5 | No errors, consistent, polished |

**Target:** 4.5+ average = Production-ready

**Calculation:**

```
Total Score = (Structure + Frontmatter + Content + Documentation + Quality) / 5
```

**Ratings:**

- **5.0** = Perfect, exemplary
- **4.5-4.9** = Excellent, ready to publish
- **4.0-4.4** = Good, minor improvements needed
- **3.0-3.9** = Acceptable, needs refinement
- **< 3.0** = Not ready, major work needed

---

## Common Issues

### Critical Issues (Must Fix)

| Issue               | Detection      | Fix                               |
| ------------------- | -------------- | --------------------------------- |
| No SKILL.md         | File missing   | Create SKILL.md                   |
| Invalid YAML        | Syntax error   | Fix YAML syntax                   |
| Missing name        | Field absent   | Add `name:` to frontmatter        |
| Missing description | Field absent   | Add `description:` to frontmatter |
| No examples         | No `<example>` | Add example blocks                |

### Major Issues (Should Fix)

| Issue                 | Detection     | Fix                       |
| --------------------- | ------------- | ------------------------- |
| SKILL.md > 1000 lines | File too long | Split into references/    |
| Vague description     | Generic text  | Be specific, add triggers |
| No README             | File missing  | Create README.md          |
| No LICENSE            | File missing  | Add LICENSE file          |
| Broken links          | Link checker  | Fix or remove links       |

### Minor Issues (Nice to Fix)

| Issue             | Detection               | Fix                   |
| ----------------- | ----------------------- | --------------------- |
| No version        | metadata.version absent | Add versioning        |
| No tags           | metadata.tags absent    | Add relevant tags     |
| No CHANGELOG      | File missing            | Create CHANGELOG.md   |
| Long references   | Files > 600 lines       | Split topics          |
| Missing examples/ | No examples             | Add concrete examples |

---

## Automated Checks (Optional)

### YAML Syntax

```bash
# Python YAML validation
python3 << 'EOF'
import yaml
import sys

with open('SKILL.md', 'r') as f:
    content = f.read()

parts = content.split('---')
if len(parts) < 3:
    print("ERROR: Invalid frontmatter format")
    sys.exit(1)

try:
    data = yaml.safe_load(parts[1])
    print("✓ YAML syntax valid")

    # Check required fields
    if 'name' not in data:
        print("ERROR: Missing 'name' field")
        sys.exit(1)
    if 'description' not in data:
        print("ERROR: Missing 'description' field")
        sys.exit(1)

    print("✓ Required fields present")
    print(f"✓ Skill: {data['name']}")

except Exception as e:
    print(f"ERROR: {e}")
    sys.exit(1)
EOF
```

### Link Checking

```bash
# Check for broken internal links
grep -r '\[.*\](references/.*\.md)' SKILL.md | while read line; do
    file=$(echo "$line" | sed 's/.*(\(.*\))/\1/')
    if [ ! -f "$file" ]; then
        echo "BROKEN LINK: $file"
    fi
done
```

### File Size Check

```bash
# Check SKILL.md size
lines=$(wc -l < SKILL.md)
if [ $lines -gt 500 ]; then
    echo "WARNING: SKILL.md has $lines lines (>500)"
fi
```

---

## Manual Review Checklist

### Final Pre-Publish Check

- [ ] Read SKILL.md start to finish
- [ ] Test all code examples
- [ ] Verify all links work
- [ ] Check for typos/grammar
- [ ] Ensure examples make sense
- [ ] Confirm file structure correct
- [ ] Test skill activation (if possible)
- [ ] Review with fresh eyes after 24h

### Peer Review (Recommended)

- [ ] Another person reads skill
- [ ] Another person tries using skill
- [ ] Feedback incorporated
- [ ] Tested on target platform

---

## Post-Validation

### After Passing Validation

1. **Version** (if not done)

   ```yaml
   metadata:
     version: "1.0.0"
   ```

2. **Tag** (if using Git)

   ```bash
   git tag -a v1.0.0 -m "Release v1.0.0"
   git push --tags
   ```

3. **Publish**
   - Push to GitHub
   - Share in community
   - Add to skill directories

4. **Maintain**
   - Update CHANGELOG for changes
   - Bump version on updates
   - Respond to issues/feedback

---

## Quick Pass/Fail

**Minimum to pass:**

✅ **PASS if:**

- SKILL.md exists
- Valid YAML frontmatter
- Has name and description
- Description has examples
- All English content
- No broken structure

❌ **FAIL if:**

- Any critical requirement unchecked
- YAML syntax invalid
- Missing required fields
- No examples in description
- Content not in English
- Executable scripts present

---

## Summary

Use this checklist **before sharing** your skill. A validated skill:

- Works correctly
- Is easy to understand
- Follows standards
- Can be maintained
- Helps the community

**Target:** All critical items checked, 4.5+/5.0 score on rubric.
