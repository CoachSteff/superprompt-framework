# Operational Workflow: Cursor & GitHub

**How to store, version, and share superprompts in a team or personal workflow.**

This guide covers: file organization, naming conventions, commit messages, and a 5-step workflow from idea to merged pattern.

---

## File Organization

Store superprompts in a structured repo with these conventions:

```
/framework/
  patterns.md         # Pattern library (reusable reasoning structures)
  template.md         # Canonical template
  evaluation.md       # Rubric for scoring prompts

/examples/
  coaching-reflection.md
  blog-writing.md
  deep-research.md
  image-generation.md
  keyword-research.md
  documentation-cleanup.md
  research-synthesis.md
  example-mode-a-enhancement.md
  example-mode-b-creation.md

/docs/
  mental-model.md     # Conceptual foundation
  faq.md              # Common questions
  quick-start.md      # 10-line getting started guide
  workflow.md         # This file

README.md             # Overview and navigation
PROMPTS.md            # Index of all prompts with tags
```

---

## Naming Conventions

**For prompt files:**
- Use kebab-case: `coaching-reflection.md`, `blog-writing.md`
- Name after the task, not the tool: `documentation-cleanup.md` (not `gpt-doc-fixer.md`)
- Keep names descriptive and searchable: `research-synthesis.md` (not `example5.md`)

**For patterns:**
- Store all patterns in `/framework/patterns.md` as sections
- Use Title Case for pattern names: `Decomposition`, `Role Mesh`, `Counter-Case Probing`

---

## Commit Message Style

Use conventional commits for clarity and searchability:

```
feat: Add Counter-Case Probing pattern
fix: Correct evaluation rubric scoring scale
docs: Update quick start with new examples
refactor: Reorganize pattern library by category
```

**Conventional commit types:**
- `feat`: New pattern, template, or example
- `fix`: Correction to existing prompt or documentation
- `docs`: Documentation updates (README, FAQ, guides)
- `refactor`: Restructure without changing functionality
- `chore`: Maintenance (file cleanup, typo fixes)

---

## 5-Step Workflow: From Idea to Merged Pattern

### Step 1: Draft the Prompt

Start in Cursor or your editor of choice. Use the canonical template from `/framework/template.md` as your starting point.

**What to include:**
- Clear INTENT with success criteria
- Rich CONTEXT with examples and constraints
- Structured REASONING POLICY with numbered steps
- Specific OUTPUT format or schema
- SELF-CHECK to verify quality

**Tip:** Don't try to make it perfect on the first pass. Just get the structure in place.

---

### Step 2: Test the Prompt

Run your superprompt in at least two AI tools (Claude, GPT, Gemini, Llama) to verify it's tool-agnostic.

**What to check:**
- Does it produce the desired output consistently?
- Are there formatting issues or ambiguities?
- Does it handle edge cases (missing context, unclear input)?

**If it fails:** Revise the REASONING POLICY or add constraints. Use the evaluation rubric to identify weak axes.

---

### Step 3: Score with the Rubric

Use the evaluation rubric from `/framework/evaluation.md` to score your prompt on six axes:

1. Goal Fit
2. Faithfulness to Context
3. Reasoning Quality
4. Constraint Compliance
5. Usefulness of Output
6. Reusability

**Pass threshold:** ≥3 on all axes.

If any axis scores below 3, revise before proceeding to Step 4.

---

### Step 4: Document and Tag

Add your prompt to the appropriate folder:

- **Reusable patterns** → `/framework/patterns.md` (as a new section)
- **Complete examples** → `/examples/your-prompt-name.md`

Add an entry to `PROMPTS.md` with tags for discoverability:

```markdown
## coaching-reflection.md
**Tags:** coaching, leadership, reflection, monthly-review  
**Pattern used:** Critique–Revise Loop  
**Description:** Help leaders reflect on their month and identify one concrete action to improve.
```

---

### Step 5: Commit and Share

Commit your prompt with a conventional commit message:

```bash
git add examples/your-prompt-name.md PROMPTS.md
git commit -m "feat: Add leadership reflection prompt with critique-revise pattern"
git push origin main
```

**If working in a team:** Open a pull request and tag a reviewer. Include:
- A brief description of what the prompt does
- Which pattern(s) it uses
- A sample output (optional but helpful)

---

## PROMPTS.md Index

The `PROMPTS.md` file serves as a searchable index of all prompts in the repo. Each entry should include:

- **Filename and path**
- **Tags** (comma-separated for filtering)
- **Pattern used** (if applicable)
- **One-line description**

**Example:**

```markdown
# SuperPrompt Index

## Examples

### coaching-reflection.md
**Path:** `/examples/coaching-reflection.md`  
**Tags:** coaching, leadership, reflection, monthly-review  
**Pattern:** Critique–Revise Loop  
**Description:** Help leaders reflect on their month and identify one concrete action to improve.

### blog-writing.md
**Path:** `/examples/blog-writing.md`  
**Tags:** content-creation, writing, marketing  
**Pattern:** Critique-Revise Loop  
**Description:** Create engaging, well-structured blog posts for professional audiences.

## Patterns

### Decomposition
**Path:** `/framework/patterns.md#decomposition`  
**Tags:** problem-solving, planning, complexity  
**Description:** Break complex problems into 3-5 independent sub-problems, solve separately, then synthesize.

### Role Mesh (Multi-Expert)
**Path:** `/framework/patterns.md#role-mesh`  
**Tags:** multi-perspective, evaluation, critique  
**Description:** Analyze a problem from multiple expert perspectives to surface tensions and trade-offs.
```

---

## Claude Skill Integration

The repository ships with a Claude Agent Skill that scaffolds CRAFTER-compliant superprompts. Use it when working in Claude Code or the Claude Agent SDK.

### Setup
1. Copy the `.claude/skills/crafter-superprompt/` directory into your Claude-enabled project (files are already included at the repo root).
2. Ensure the code execution tool is enabled for the workspace.
3. **Claude Code:** Claude automatically discovers skills placed in `.claude/skills/`. No additional configuration is required once the folder is present.
4. **Claude Agent SDK:** Add `"Skill"` to your `allowed_tools` array and keep the skill directory at `.claude/skills/` so the runtime can load it.

### Usage Tips
- Trigger the skill when you need to author or refine a superprompt using the CRAFTER structure.
- Leverage progressive disclosure: the core instructions live in `SKILL.md`; the detailed checklist resides in `CRAFTER-CHECKLIST.md` and is only loaded when required.
- After the skill produces a draft, run the checklist to confirm every component is satisfied and append the attribution footer.

### Security & Maintenance
- Install skills only from trusted sources; review bundled scripts before use.
- Skills run without network access and cannot install new packages—plan your workflow accordingly.
- If the CRAFTER specification changes (for example, a new component revision), update both `SKILL.md` and the checklist so the guidance stays aligned.

---

## Safety Note: Refusal Rules

Superprompts should include explicit refusal rules in the REASONING POLICY to prevent harmful outputs.

**Examples of refusal rules:**
- "Refuse to produce outputs that could be used to manipulate or coerce."
- "Refuse to make claims not supported by the provided sources."
- "Refuse to generate content that violates the style guide."

When designing refusal rules:
- Make them specific and actionable
- Explain *why* the refusal matters (not just "don't do X")
- Test edge cases: what happens if someone tries to bypass the rule?

---

## IP and Licensing

All superprompts in this repo are licensed **CC-BY 4.0** (Creative Commons Attribution 4.0 International).

**What this means:**
- You can use, modify, and share any superprompt
- You must attribute the original creator: Steff Vanhaverbeke (coachsteff.live)
- You can use superprompts in commercial projects

**When contributing:**
- By submitting a prompt, you agree to license it under CC-BY 4.0
- You retain copyright but grant others the right to use your work with attribution
- If you're adapting someone else's prompt, credit them in your file

---

## Quick Reference: Common Commands

```bash
# Create a new branch for your prompt
git checkout -b feat/your-prompt-name

# Add your files
git add examples/your-prompt-name.md PROMPTS.md

# Commit with conventional message
git commit -m "feat: Add [description]"

# Push and open a pull request
git push origin feat/your-prompt-name
```

---

## License

CC-BY 4.0 · Steff Vanhaverbeke · [coachsteff.live](https://coachsteff.live)
