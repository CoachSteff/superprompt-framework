# Frequently Asked Questions (FAQ)

**Common questions about the SuperPrompt Framework.**

---

## What is a superprompt?

A superprompt is a structured prompt that acts as a cognitive contract between you and an AI model. It specifies what to think about (context), how to think (reasoning policy), and what to produce (output specification).

It's not a longer prompt. It's a **designed thinking interface** that creates predictable, reusable results.

---

## What isn't a superprompt?

A superprompt is not:

- **A longer prompt:** Length doesn't matter. Structure does.
- **A magic spell:** Superprompts don't guarantee perfect outputs, but they make outputs more consistent and debuggable.
- **Tool-specific:** Superprompts should work across AI tools (Claude, GPT, Gemini, Llama).
- **One-size-fits-all:** Different tasks need different structures. Use patterns from the pattern library to adapt.

---

## How long should a superprompt be?

As long as it needs to be to achieve the intent. Some tasks need 100 words; others need 500. The goal is clarity, not brevity or length.

**Rule of thumb:** If your prompt scores ≥3 on all six axes of the evaluation rubric, it's the right length.

---

## Can I use superprompts in Cursor, GitHub Copilot, or other coding tools?

Yes. Superprompts work in any tool that accepts natural language instructions. The template is tool-agnostic by design.

In Cursor, you can use superprompts for tasks like:
- Code refactoring
- Documentation generation
- Test case creation
- Architecture review

See the [documentation cleanup example](../examples/documentation-cleanup.md) for a code-adjacent use case.

---

## How do I adapt a superprompt to a new task?

1. Start with the canonical template from [template.md](template.md)
2. Replace placeholders with your specifics (intent, context, reasoning policy, output)
3. Test it in your AI tool
4. If it fails, use the evaluation rubric to debug

**Quick customization levers:**
- Change the **tone** (warm, sharp, formal)
- Add **refusal rules** to constrain outputs
- Include a **JSON schema** for structured data

---

## What's the difference between a superprompt and a pattern?

- **Superprompt:** A complete prompt ready to use for a specific task (e.g., "design a workshop")
- **Pattern:** A reusable reasoning structure you can plug into any superprompt (e.g., "Decomposition," "Role Mesh")

Think of patterns as modular components you mix and match inside superprompts.

---

## How do I know if my superprompt is good?

Use the [evaluation rubric](evaluation.md) to score your prompt on six axes:

1. Goal Fit
2. Faithfulness to Context
3. Reasoning Quality
4. Constraint Compliance
5. Usefulness of Output
6. Reusability

If all axes score ≥3, your superprompt is ready to use.

---

## What are common pitfalls when writing superprompts?

**1. Vague intent:** "Write a blog post" is too vague. Add success criteria: "Write a 600-word blog post that helps mid-level managers understand why AI adoption requires new skills."

**2. Missing context:** If the model doesn't have the facts it needs, it will guess. Add examples, constraints, and domain knowledge to the CONTEXT section.

**3. No reasoning policy:** Without explicit steps, the model will improvise. Define how you want it to think.

**4. Generic constraints:** "Be concise" is too vague. Say "500 words max" or "3 bullet points."

**5. Forgetting the self-check:** Always include a SELF-CHECK section to verify outputs before finalizing.

---

## Can I combine patterns?

Yes. Patterns are composable. For example:

- Use **Decomposition** to break a problem into parts, then apply **Role Mesh** to each part to get multi-expert feedback.
- Use **Counter-Case Probing** to stress-test an idea, then apply **Critique–Revise Loop** to refine it.

See the [pattern library](patterns.md) for more examples.

---

## How do I handle edge cases or unexpected inputs?

Add refusal rules to your REASONING POLICY. For example:

- "If you don't have enough context to answer, ask for clarification instead of guessing."
- "Refuse to produce outputs that could be used to manipulate or coerce."
- "If the input is ambiguous, request clarification before proceeding."

Refusal rules make your prompts more robust to edge cases.

---

## What if my superprompt works in Claude but fails in GPT?

Your instructions may be too implicit. Different models interpret instructions differently.

**How to fix:**
- Make steps in REASONING POLICY more explicit (numbered, sequential)
- Add examples to CONTEXT to show what you mean
- Test with both models and note where they diverge
- Adjust the prompt to work for the lowest common denominator

---

## Can I use superprompts for creative tasks (writing, art, design)?

Yes. Superprompts work for any task where you need structured thinking. Creative tasks benefit from:

- **Style Transfer** pattern (translate formal to casual, academic to conversational)
- **Perspective Shift** pattern (reframe a problem from a new angle)
- **Critique–Revise Loop** pattern (iterative refinement)

See the [coaching reflection example](../examples/coaching-reflection.md) for a creative application.

---

## How do I share superprompts with my team?

Follow the [workflow guide](workflow.md):

1. Save your prompt to a shared repo (GitHub, Notion, etc.)
2. Add metadata (tags, description, pattern used) to a PROMPTS.md index
3. Use conventional commit messages for versioning
4. License your prompts with CC-BY 4.0 for open sharing

---

## What license should I use for my superprompts?

This framework uses **CC-BY 4.0** (Creative Commons Attribution 4.0 International).

**What this means:**
- Anyone can use, modify, and share your prompts
- They must attribute you as the creator
- You retain copyright but grant others usage rights

This keeps superprompts open and reusable.

---

## Can I use superprompts for commercial projects?

Yes. The CC-BY 4.0 license allows commercial use. Just provide attribution to the original creator (Steff Vanhaverbeke / coachsteff.live for this framework, or whoever created the specific prompt).

---

## Where can I find more examples?

Check the `/examples` folder for nine complete superprompts:

- [Coaching Reflection](../examples/coaching-reflection.md)
- [Blog Writing](../examples/blog-writing.md)
- [Deep Research](../examples/deep-research.md)
- [Image Generation](../examples/image-generation.md)
- [Keyword Research](../examples/keyword-research.md)
- [Documentation Cleanup](../examples/documentation-cleanup.md)
- [Research Synthesis](../examples/research-synthesis.md)
- [Mode A: Enhancement](../examples/example-mode-a-enhancement.md)
- [Mode B: Creation](../examples/example-mode-b-creation.md)

---

## How do I contribute a new pattern or example?

Follow the 5-step workflow in [workflow.md](workflow.md):

1. Draft your prompt
2. Test it in at least two AI tools
3. Score it with the evaluation rubric
4. Document it with tags and metadata
5. Commit with a conventional commit message and open a pull request

---

## Who created the SuperPrompt Framework?

The framework was created by **Steff Vanhaverbeke**, an AI Adoption Coach and co-founder of The House of Coaching. Steff specializes in the human side of AI adoption—helping professionals build the cognitive capabilities that matter most in an AI-driven world.

Learn more at [coachsteff.live](https://coachsteff.live).

---

## Where can I get help or report issues?

- **GitHub Issues:** Open an issue on the [repo](https://github.com/CoachSteff/superprompt-framework)
- **Email:** steff@coachsteff.live
- **LinkedIn:** [Steff Vanhaverbeke](https://linkedin.com/in/steffvanhaverbeke)

---

## License

CC-BY 4.0 · Steff Vanhaverbeke · [coachsteff.live](https://coachsteff.live)
