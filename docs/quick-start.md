# Quick Start Guide

**Get started with the SuperPrompt Framework in 10 steps.**

---

## 1. Understand the Core Idea

A superprompt is a structured cognitive interface between your intent and AI reasoning. It's not about making prompts longer—it's about making them more predictable and reusable.

Read the [mental model](mental-model.md) (5 minutes).

---

## 2. Copy the Template

The canonical template is your starting point. Copy it from [template.md](template.md) and paste it into your AI tool of choice (Claude, GPT, Gemini, Llama).

---

## 3. Fill in the Placeholders

Replace the template placeholders with your specifics:

- **INTENT:** What does success look like?
- **CONTEXT:** What does the model need to know?
- **REASONING POLICY:** How should it think?
- **OUTPUT:** What should it produce?

---

## 4. Run It

Paste your completed superprompt into your AI tool and run it. Check the output: Does it match your intent?

---

## 5. If It Fails, Debug with the Rubric

Use the [evaluation rubric](evaluation.md) to identify which axis scored low (Goal Fit, Faithfulness, Reasoning Quality, Constraint Compliance, Usefulness, Reusability).

Fix the weak axis by revising the corresponding section of your prompt.

---

## 6. Make It Reusable

Replace specifics with placeholders. Instead of "design a workshop for managers," write "design a `<format>` for `<audience>`."

This makes your prompt reusable across contexts.

---

## 7. Test Across Tools

Run your prompt in at least two AI tools to verify it's tool-agnostic. If it works in Claude but fails in GPT, your instructions may be too implicit—make them more explicit.

---

## 8. Browse the Pattern Library

If your prompt needs a specific reasoning structure, check the [pattern library](patterns.md) for reusable patterns like Decomposition, Role Mesh, or Counter-Case Probing.

Copy the structure tweak into your REASONING POLICY.

---

## 9. Look at Examples

See nine complete, copy-ready superprompts in the `/examples` folder:

- [Coaching Reflection](../examples/coaching-reflection.md)
- [Blog Writing](../examples/blog-writing.md)
- [Deep Research](../examples/deep-research.md)
- [Image Generation](../examples/image-generation.md)
- [Keyword Research](../examples/keyword-research.md)
- [Documentation Cleanup](../examples/documentation-cleanup.md)
- [Research Synthesis](../examples/research-synthesis.md)

---

## 10. Share or Save Your Prompt

If your prompt works well, save it to your personal knowledge base or contribute it to this repo. Follow the [workflow guide](workflow.md) for instructions on naming, tagging, and committing prompts.

---

## What's Next?

- **Deep dive:** Read the [FAQ](faq.md) to understand common questions and pitfalls.
- **Contribute:** Add your own patterns or examples to the repo.
- **Practice:** The best way to learn superprompting is to use it. Start with a real task you have this week and build a superprompt for it.

---

## License

CC-BY 4.0 · Steff Vanhaverbeke · [coachsteff.live](https://coachsteff.live)
