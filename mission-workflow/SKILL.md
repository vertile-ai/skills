---
name: mission-workflow
description: Run non-trivial coding missions with a main-agent, worker-agent, and reviewer-agent loop. Use when the user asks for mission workflow, 3-agent workflow, worker/reviewer collaboration, independent review before completion, unbiased validation, fresh-context implementation/review passes, or high-confidence execution of a coding task.
---

# Mission Workflow

## Overview

Use this skill to execute a coding mission with one coordinating main agent, one implementation worker, and one independent reviewer. The goal is to reduce tunnel vision: the worker builds, the reviewer validates from fresh context, and the main agent owns scope, decisions, integration, and final truth.

Do not use this workflow for tiny one-command tasks, direct explanations, edits where spawning agents would add ceremony without improving correctness, or agent environments that cannot spawn or coordinate subagents.

## Scale Policy

Choose the smallest mission shape that gives independent implementation and review:

- **Standard mission:** one main agent, one executor worker, and one independent reviewer.
- **High-risk mission:** one executor worker plus the most relevant specialist reviewer, such as `security-reviewer`, `test-engineer`, `vision`, or `verifier`.
- **Large mission:** split into concrete slices and run the worker/reviewer loop per slice instead of creating one broad task.
- **Parallel mission:** use multiple workers only when write scopes are disjoint and the main agent can integrate the results without shared-file conflicts.

Default to the standard mission unless the task has obvious independent slices or a specific risk profile.

## Roles

### Main agent

- Read the repo and user request first.
- Define the task boundary, acceptance criteria, and verification evidence.
- Give the worker only the context needed to implement the current slice.
- Give the reviewer only the context needed to validate the worker's result.
- Decide whether the work is accepted, needs another worker pass, or needs main-agent intervention.
- Perform final verification and report the outcome to the user.

### Worker agent

- Implement the assigned slice.
- Follow existing repo patterns and avoid unrelated refactors.
- Run relevant local checks where possible.
- Report changed files, verification commands, failures, and unresolved risks.

### Reviewer agent

- Review from fresh context after worker completion.
- Prioritize behavioral bugs, integration risks, missing tests, weak tests, security issues, and user-visible regressions.
- Verify the quality of tests and artifacts, not only whether commands passed.
- For UI work, inspect screenshots or run browser checks when available.
- State a clear verdict: `approved`, `needs changes`, or `blocked`.

## Workflow

1. **Frame the task.** Restate the goal as acceptance criteria and decide the first implementation slice. Keep slices small enough that review can be concrete.

2. **Start a fresh worker.** Use available subagent or multi-agent tools. Prefer an `executor` role for implementation. Use `fork_context: false` or equivalent fresh-context behavior unless the tool requires inherited context.

3. **Worker implements.** Ask the worker to modify files and run relevant checks. The worker should not be told the expected review outcome.

4. **Start a fresh reviewer.** Use a reviewer/verifier/test-engineer/security-reviewer role that matches the risk. Clear prior context for the reviewer when the tooling supports it. Give the reviewer the context packet below. Do not leak your preferred conclusion.

5. **Review the result.** Treat reviewer output as evidence, not authority. If the reviewer finds valid issues, send a focused follow-up task to a fresh or reset worker. If the reviewer misses something obvious, the main agent must still catch it.

6. **Iterate until accepted.** Repeat worker and reviewer passes until the implementation satisfies the acceptance criteria or a real blocker remains.

7. **Final verification.** The main agent runs or inspects the final checks directly. Do not claim completion only because worker or reviewer said it is done.

8. **Report concisely.** Summarize what changed, what passed, where artifacts are, and any residual risk.

## Dispatch Protocol

Before starting agents, write down:

- `slice`: the bounded piece of work for this pass.
- `owner`: files, modules, or responsibility owned by the worker.
- `acceptance`: concrete checks the reviewer can validate.
- `evidence`: commands, screenshots, logs, or manual checks expected at the end.
- `stop condition`: when to stop iterating and ask the user or escalate to main-agent design work.

Use one worker per slice unless the write scopes are disjoint. Use one reviewer per completed slice. For large tasks, repeat the protocol across slices instead of creating one vague mega-task. Keep parallel workers to three or fewer by default unless the user explicitly requests broader parallelism.

When Codex exposes `multi_agent_v1`, use it as the canonical handoff mechanism:

- Worker: `spawn_agent` with `agent_type: "executor"`, `fork_context: false`, and the worker brief. Use `agent_type: "worker"` only inside active team/swarm runtimes that define `worker` as the execution surface.
- Reviewer: `spawn_agent` with `agent_type: "code-reviewer"`, `"verifier"`, `"test-engineer"`, `"security-reviewer"`, or `"vision"` depending on the risk, `fork_context: false`, and the reviewer brief.
- Wait only when the main agent needs the result for the next step.
- Close completed agents when their result has been integrated or rejected.

If agents from a prior slice exist, close them before a new unbiased pass unless their retained context is explicitly needed. A strict reset means a new agent id, no forked conversation context, and a prompt built from the context packet rather than chat history.

## Context Packet

Give the worker:

- The user goal and current slice.
- Write scope and files/modules they may touch.
- Relevant repo commands, setup notes, and known constraints.
- Existing patterns to preserve.
- Required report format.

Give the reviewer:

- The user goal and acceptance criteria.
- The final diff or exact files changed.
- Commands the worker ran and their results.
- Screenshots, logs, traces, or external artifacts relevant to the claim.
- Known residual risks reported by the worker.

Do not give the reviewer:

- The main agent's preferred verdict.
- Hidden expected answers.
- Speculation about the likely bug unless it is necessary to reproduce.
- Long conversation history when a concise goal and diff would suffice.

## Fresh-Context Rules

- Start a new worker and reviewer for each distinct slice when practical.
- Do not reuse a reviewer as a worker for the same slice.
- Do not give reviewer prompts that include the worker's excuses, your diagnosis, or the intended fix unless those facts are required to reproduce the issue.
- Prefer raw evidence: diffs, file paths, screenshots, logs, command outputs, failing tests, and acceptance criteria.
- If the user explicitly asks for maximum unbiased review, close or reset prior subagent context before the next pass.

## Worker Brief Template

```text
You are the worker agent for this coding task.

Goal:
<user-facing goal>

Scope:
<files/features to touch, plus boundaries>

Acceptance criteria:
- <criterion>
- <criterion>

Repo context:
- <important commands, paths, patterns>

Implement the slice, run relevant checks, and report:
- files changed
- commands run and results
- unresolved risks or blockers
```

## Reviewer Brief Template

```text
You are the independent reviewer for this coding task.

Goal:
<user-facing goal>

Artifacts to inspect:
- <diff/files/screenshots/test output>

Acceptance criteria:
- <criterion>
- <criterion>

Review for:
- behavioral correctness
- integration risks
- missing or weak tests
- UI fidelity and screenshots when applicable
- security, data, or deployment risks when applicable

Return:
- verdict: approved | needs changes | blocked
- findings ordered by severity with file/line references when possible
- verification gaps
```

## Review Standards

- Prefer live-path verification over mocked-only proof when the user-facing behavior depends on integration.
- Treat tests that only check implementation details as weak evidence.
- For backend or AI work, verify error handling, schema validation, rate limits, secret handling, and production failure modes.
- For frontend work, verify responsive states, empty/loading/error states, and screenshot evidence when visual fidelity matters.
- For mobile work, distinguish native proof from web-simulated proof.
- For deployment work, separate "configured" from "successfully deployed and reachable."

## Iteration And Escalation

- If reviewer verdict is `approved`, the main agent still runs or inspects final verification before completion.
- If reviewer verdict is `needs changes`, send only the valid findings to a fresh or reset worker with a narrow fix scope.
- If the same class of issue survives two worker passes, the main agent must stop and re-diagnose the design or tests before delegating again. "Same class" means the same failing behavior, same missing proof type, same architectural concern, or same reviewer objection remains after a fix attempt.
- If reviewer verdict is `blocked`, identify the missing input, environment problem, or external dependency. Work around it when safe; otherwise ask the user with a concrete blocker.
- Do not run endless loops. After three implementation/review cycles on the same slice, either resolve locally as main agent or report the blocker and next best step.

## Evidence Checklist

Choose the relevant evidence for the task. The final answer should name what was actually verified.

- **Static correctness:** typecheck, lint, format, schema validation, or compile.
- **Unit behavior:** focused unit tests for edge cases and failure modes.
- **Integration behavior:** API route, database, filesystem, queue, SDK, or service checks on the real path when practical.
- **UI behavior:** browser/mobile interaction checks plus screenshots for important states.
- **Security/data:** auth boundaries, secret handling, rate limits, input validation, migrations, and rollback risks.
- **Deployment/runtime:** production build, env metadata, deployment logs, reachable URL, or smoke test.
- **Costly/external tests:** clearly separate mocked non-costly coverage from real provider or paid-path checks.

## Completion Bar

Only finish when all of these are true:

- The worker's changes are integrated in the repo.
- Reviewer findings are resolved or explicitly accepted as residual risk.
- Main agent has independently run or inspected final verification.
- The final evidence checklist has at least one task-appropriate proof item, and any skipped high-value proof is named with the reason.
- Final response includes concrete evidence, not just a process summary.

Use this final evidence format when the task is more than a tiny edit:

```text
Changed:
- <files/features>

Verified:
- <command or artifact>: <result>

Reviewed:
- worker: <agent id or note>
- reviewer: <agent id or note>, verdict <approved | needs changes | blocked>

Residual risk:
- <none or named risk>
```
