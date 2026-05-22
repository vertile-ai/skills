# OpenAI Prompt Guidance Reference

Source incorporated: OpenAI API Prompt guidance, checked 2026-05-21.
Use the live source for exact current API details:
[OpenAI Prompt guidance](https://developers.openai.com/api/docs/guides/prompt-guidance)

This reference condenses the guide into operational rules for prompt
optimization. It is intentionally paraphrased and organized for use inside this
skill.

## GPT-5.5

Core behavior:

- Prefer shorter, outcome-first prompts over process-heavy prompt stacks.
- Re-test `low` and `medium` reasoning effort before escalating.
- Keep preambles, `phase`, and assistant-item replay rules for tool-heavy Responses workflows.
- Add explicit personality, retrieval budgets, and validation rules for customer-facing and agentic UX.
- Define what good looks like: target outcome, constraints, available evidence, and final-answer contents.
- Avoid rules that over-specify the path unless they protect a real invariant.

Personality and collaboration:

- Separate personality from collaboration style.
- Personality sets tone, warmth, directness, formality, humor, empathy, and polish.
- Collaboration style sets when to ask, assume, act proactively, give context, check work, and handle uncertainty.
- Keep both short. They should not replace task goals, tool rules, success criteria, or stopping conditions.

Preambles:

- For long, streaming, or tool-heavy tasks, ask for a short visible preamble that acknowledges the task and states the first step.
- In runtimes with message phases, mark preambles as intermediate, not final.

Outcome and stopping:

- Describe the destination rather than every step.
- Use absolute words only for true invariants.
- Use decision rules for search, clarification, tool use, iteration, and assumptions.
- Add explicit stopping conditions.
- Define what to do when evidence is missing or insufficient.

Formatting:

- Use `text.verbosity` where available.
- State output shape and audience explicitly.
- Use heavier structure only when comprehension or product UI requires it.
- For editing and rewrites, specify what to preserve before asking for improvement.

Grounding and retrieval:

- Define what must be supported by citations.
- Define what counts as enough evidence.
- Treat absence of evidence as unknown unless the evidence boundary supports a factual negative.
- Add a retrieval budget as a search stopping rule.

Creative drafting:

- Separate source-bound claims from creative framing.
- Allow creative language for narrative, voice, and polish only where factual claims are either sourced or clearly not factual.

Frontend and visual work:

- Include product/user context, design-system alignment, expected states, responsive behavior, and visual verification.
- Avoid generic generated-UI defaults: decorative gradients, nested cards, empty hero pages, visible "how to use" text, missing states, and broken responsive layouts.

Validation:

- Ask the model to check work when tools can validate the result.
- For code, name concrete validation commands.
- For visual artifacts, render and inspect screenshots.
- For plans, make steps traceable to requirements and constraints.

Responses API phase:

- Use `phase` for long-running or tool-heavy workflows with preambles, repeated tool calls, or intermediate updates.
- Preserve original `phase` values when replaying assistant output items.
- Prefer `previous_response_id` when possible.

Suggested complex prompt shape:

1. Role and outcome.
2. Context and available evidence.
3. Constraints and invariants.
4. Personality and collaboration style, if needed.
5. Tool, retrieval, and citation rules.
6. Validation and stopping conditions.
7. Output format.

## Prompt Optimizer Checklist

- State the GPT-5.5 runtime controls.
- Replace process-heavy scaffolding with outcome, constraints, evidence, and output requirements.
- Preserve hard rules only for invariants.
- Add decision rules for search, clarification, tool use, and persistence.
- Define evidence boundaries and citation format when factual grounding matters.
- Define retrieval budget for research tasks.
- Define strict output format and no-extra-prose rules for parse-sensitive outputs.
- Add validation when there is a real way to check the result.
- Add completion criteria and blocked-item reporting for multi-step work.
- Preserve `phase` and replay semantics for long Responses API workflows.
- Keep final prompts compact enough for the target surface and eval them after each meaningful change.
