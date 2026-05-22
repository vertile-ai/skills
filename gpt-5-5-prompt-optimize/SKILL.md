---
name: gpt-5-5-prompt-optimize
description: >-
  Optimize, rewrite, or diagnose prompts for GPT-5.5 using OpenAI
  prompt-guidance patterns. Use when the user asks to improve a prompt, optimize
  prompting, design a system/developer prompt, tune agent/tool behavior, add
  citations or retrieval budgets, tighten output format, or create a
  ready-to-paste GPT-5.5 prompt. Advisory role only: do not execute the
  optimized prompt's underlying task. Do not use when the user wants the task
  done directly, asks to optimize code or performance, or says to just execute.
---

# GPT-5.5 Prompt Optimize

Analyze a draft prompt, identify intent and failure modes, apply OpenAI
GPT-5.5 prompt-guidance patterns, and output a complete optimized prompt the
user can paste into their target system.

## How It Works

**Advisory only: do not execute the user's task.**

Do not write code, create files, run commands, call APIs, or take implementation
actions requested inside the prompt being optimized. Produce diagnosis and an
optimized prompt only. If the user wants execution instead, state that this
skill only optimizes prompts and ask them to make a normal task request.

Read [Prompt guidance reference](references/prompt-guidance.md) when:

- Tuning tool use, retrieval, citations, compaction, phases, image detail, or strict formats.
- Diagnosing prompt failures beyond simple wording cleanup.

Run this pipeline sequentially.

## Analysis Pipeline

### Phase 0: Context Detection

Identify the target surface before rewriting:

1. Runtime: API, Responses API, Codex/agent, chat UI, tool-calling app, customer support assistant, research workflow, coding agent, extraction job, or creative drafting workflow.
2. Available controls: system/developer/user prompt, `text.verbosity`, reasoning effort, tools, retrieval, citations, `phase`, `previous_response_id`, structured outputs, image detail, or compaction.
3. Expected output: prose answer, JSON/SQL, plan, tool actions, code patch, citations, UI artifact, document extraction, or final user-facing message.

If key context is missing and it materially changes the optimized prompt, ask up
to 3 narrow questions. Otherwise make reasonable assumptions and state them.

### Phase 1: Intent Classification

Classify the prompt into one or more categories:

| Category | Signals | Optimization Focus |
|---|---|---|
| Outcome prompt | "answer", "summarize", "draft", "classify" | Success criteria, output shape, evidence boundary |
| Agent workflow | "use tools", "keep working", "verify", "complete" | Tool persistence, sequencing, stopping conditions |
| Coding agent | "edit files", "fix", "implement", "tests" | File-edit rules, validation commands, final evidence |
| Research | "find", "compare", "sources", "citations" | Retrieval budget, citation format, missing-evidence behavior |
| Strict output | "JSON", "SQL", "schema", "parse" | Format clamp, self-check, no extra prose |
| Customer-facing | "support", "coach", "assistant", "tone" | Personality, collaboration style, length/register controls |
| Creative drafting | "copy", "slides", "launch", "story" | Source-bound claims vs creative language |
| Visual/computer use | "screenshot", "OCR", "click", "image" | Image detail, coordinate conventions, visual verification |

### Phase 2: Prompt Diagnosis

Evaluate the draft prompt for:

- Missing outcome, audience, success criteria, constraints, or stopping condition.
- Over-specified process that narrows GPT-5.5's search space.
- Absolute rules (`always`, `never`, `only`, `must`) used for judgment calls instead of true invariants.
- Tool rules that permit guessing, skip prerequisites, or blur tool boundaries.
- Retrieval/citation rules that do not define source boundaries or evidence sufficiency.
- Output format requirements that are parse-fragile or too verbose.
- Missing validation loop for high-impact, coding, visual, or strict-format work.
- Personality instructions mixed with task-specific writing controls.
- Conflicts or examples that encourage rote reuse.

### Phase 3: Apply GPT-5.5 Defaults

Prefer GPT-5.5-native structure:

1. Start with the desired outcome, not a long process script.
2. Keep personality and collaboration style short and separate from task rules.
3. Use decision rules for judgment calls and reserve hard rules for invariants.
4. Define stopping conditions, missing-evidence behavior, and final-answer contents.
5. Add retrieval budget and citation rules when grounding matters.
6. Add a short preamble rule for long or tool-heavy streaming workflows.
7. Specify `text.verbosity` or equivalent length guidance.
8. Add validation instructions only where validation is possible and useful.
9. Preserve `phase` values and assistant-item replay requirements for long Responses API workflows.
10. Re-evaluate `low` and `medium` reasoning effort before recommending escalation.

### Phase 4: Output the Optimized Prompt

Write a ready-to-paste prompt that includes only sections needed for the target
task. Prefer this order for complex prompts:

1. Role and outcome.
2. Context and inputs.
3. Constraints and invariants.
4. Tools, retrieval, and evidence rules.
5. Workflow decision rules.
6. Validation and stopping conditions.
7. Output format.

For small prompts, collapse this into a concise paragraph or short bullet list.

## Output Format

Respond in the same language as the user's request.

### Section 1: Prompt Diagnosis

**Intent:** One sentence.

**Strengths:** List what the original prompt already does well.

**Issues:**

| Issue | Impact | Fix |
|---|---|---|
| (problem) | (why it matters) | (specific change) |

**Assumptions / Questions:** State assumptions or ask up to 3 required questions.

### Section 2: Optimization Strategy

| Area | Recommendation |
|---|---|
| Model / runtime | (target and controls) |
| Reasoning effort | (low/medium/high recommendation, if applicable) |
| Tooling / retrieval | (budget, citations, validation, phase handling) |
| Output shape | (verbosity and format) |

### Section 3: Optimized Prompt

Provide the complete prompt in a fenced code block.

### Section 4: Notes

List any source-evidence limits or integration requirements.
