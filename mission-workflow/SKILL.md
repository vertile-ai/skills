---
name: mission-workflow
description: Execute non-trivial coding work through a lightweight Factory-style mission with one coordinator, one implementation worker, and one independent reviewer while enforcing a smallest-working-V1 and no-overengineering policy. Use when the user asks for a mission workflow, Factory mission structure, a minimal-agent implementation/review loop, fresh-context validation, or an independent review gate around a bounded coding task.
---

# Mission Workflow

## Purpose

Apply a lightweight version of Factory's mission architecture: define correctness before implementation, give each agent one focused incentive, and validate outcomes from context independent of the implementer.

The current main agent is the coordinator; do not spawn another coordinator. For each slice, use one worker followed by one reviewer. The reviewer evaluates but never edits. This is an evaluator-optimizer loop, not an agent swarm.

## Invariants

- Define observable correctness before deciding how to implement it.
- Build the smallest end-to-end V1 that satisfies the current goal.
- Keep implementation and judgment in separate contexts.
- Give each agent one bounded goal and only relevant context.
- Prefer environment evidence over agent confidence.
- Reject complexity justified only by hypothetical future needs.
- Add agents only when the task structure justifies them.
- Keep the main agent responsible for scope, integration, and final truth.

## No Over-Engineering

Treat this as a hard mission constraint, not a style preference.

Over-engineering is any architecture, abstraction, infrastructure, failure machinery, configurability, compatibility layer, or test surface that does not change whether the current V1 can run through successfully and is not needed to prevent an immediate severe risk. A possible future requirement is not evidence.

Default to one working happy path from input to observable result. Prefer failing clearly over recovering automatically. Prefer a synchronous, local, concrete implementation over an asynchronous, distributed, generalized one. Defer optimization and hardening until real usage or an explicit requirement justifies them.

Historical compatibility is out of scope by default unless the user or the mission acceptance criteria explicitly require it. The mere existence or possibility of old records, old schemas, old API shapes, or previous behavior does not itself create a compatibility requirement. Default to the new schema and the new path directly. Do not add migrations, backfills, dual-read or dual-write paths, legacy parsers, compatibility adapters or shims, version bridges, fallback branches, old and new parallel processing, or tests and fixtures for historical formats unless compatibility is explicitly asserted.

If compatibility is required, make it its own assertion with named historical inputs and observable expected behavior, then implement the smallest mechanism that satisfies that assertion. If the new implementation would require destructive migration of unknown existing data and compatibility was not requested, stop and report the conflict rather than inventing a compatibility system.

Apply this counterfactual before keeping any non-trivial code or test:

1. If it is removed, does the current V1 happy path stop working?
2. If it is a test or validation artifact, does removing it eliminate unique evidence not already provided by running the happy path?

If both answers are no, remove or defer it. Do not keep duplicate proof merely because it may detect a hypothetical future regression.

### Defaults By Work Type

**Greenfield feature or product:** Build the smallest MVP that proves one complete user journey. Do not add corner-case coverage, retries, replay, durable queues, delivery guarantees, idempotency, deduplication, reconciliation, plugin systems, broad configuration, or speculative extension points.

**Feature in an existing product:** Implement only the requested behavior and the minimum integration needed by the current architecture. Preserve existing production invariants, but do not redesign or harden adjacent systems.

**Bug fix:** Reproduce the bug, add the narrowest useful regression check, and fix the root cause with the smallest patch. Do not refactor neighboring code, introduce a framework, or solve a wider class of hypothetical bugs.

**Refactor or cleanup:** Preserve behavior and reduce code, concepts, or coupling. Do not add an abstraction unless it removes demonstrated duplication or complexity already present. Do not combine cleanup with migrations, extensibility work, or architecture changes.

**Integration, background job, or messaging:** First prove one request, event, or job can travel through the complete chain successfully. Treat retries, replay, durable delivery, guaranteed message retention, outbox patterns, dead-letter queues, circuit breakers, exactly-once semantics, idempotency, and deduplication as separate later requirements.

**UI work:** Complete the primary interaction and the minimum visible feedback needed to understand success or failure. Do not build an exhaustive state matrix, generalized component system, theming framework, or speculative responsive variants unless required by the contract.

**Frontend-backend contract:** Define the request and response schema, implement both sides against it, and prove the real interaction runs through. Do not add consumer-driven contract tests, provider verification suites, schema snapshot tests, interface-parity tests, or duplicated fixtures merely to assert that the schema is complete. A successful real frontend-backend flow is sufficient V1 proof.

**Data model or API:** Define only the fields, endpoints, and relationships consumed by the current flow. Implement the new schema and path directly unless compatibility is explicitly asserted. Do not add event sourcing, audit history, versioning, soft deletion, generalized permissions, or compatibility layers for imagined consumers.

**Infrastructure or deployment:** Use the repository's existing path and prove one deployable instance works. Do not add high availability, multi-region support, autoscaling systems, orchestration layers, or new observability infrastructure unless explicitly required.

**Tests:** Prove the primary flow and the behavior directly changed. Add regression coverage for a reproduced bug when it provides evidence the run-through does not. Do not add redundant contract, snapshot, edge-case, property, fuzz, chaos, load, or cross-platform suites to a V1 unless they are part of acceptance.

### Complexity Admission Gate

Allow a non-trivial mechanism only when at least one of these statements is concrete and true:

- A current mission assertion cannot pass without it.
- An explicit current in-scope repository or production contract already requires it. This path never admits historical compatibility unless that compatibility is separately asserted with named historical inputs, or a reproduced in-scope failure demonstrates the need.
- A reproduced current failure demonstrates the need.
- Omitting it creates an immediate security, privacy, financial, or irreversible data-corruption risk.

Require the worker to name the qualifying statement. If none applies, remove or defer the mechanism. When the user explicitly requests durability, idempotency, replay, or another hardening property, encode it as its own assertion and implement the smallest design that proves that property.

Unknown old data alone is not enough to admit migrations, backfills, dual paths, or compatibility shims.

Basic correctness is not over-engineering: keep the code compiling, preserve current explicitly asserted in-scope contracts, avoid obvious security defects, fail visibly, and leave the repository in a testable state.

## Agent Budget

Default to at most two spawned agents for a slice:

1. One implementation worker.
2. One independent reviewer.

Run them sequentially. A specialist such as a security reviewer, test engineer, visual reviewer, or verifier replaces the generic reviewer; it does not join as an additional reviewer.

Keep the same worker for focused correction passes on the same slice unless it is stuck or its context is no longer useful. Keep one reviewer for the slice unless that reviewer edited the implementation, the scope changed materially, or the user explicitly requests a new unbiased pass.

For large work, prefer sequential slices over more agents. Add parallel workers only when all of the following are true:

- The slices have disjoint write scopes.
- Parallelism materially shortens the critical path.
- The coordinator can verify integration boundaries.
- The user or repository policy does not require the minimal two-agent shape.

Never spawn speculative researchers, planners, or multiple reviewers merely because they are available. If the environment cannot provide an independent context, execute directly and disclose that the review was not independent.

## Mission Contract

Before dispatching implementation, write a compact contract containing:

- `goal`: the user-visible outcome.
- `non-goals`: boundaries that prevent scope drift.
- `v1 boundary`: the single end-to-end path that must work now, plus the hardening explicitly deferred until later.
- `assertions`: a finite list of testable behaviors that define correctness.
- `evidence`: the command, artifact, or observation expected for each assertion.
- `constraints`: repository rules and risk boundaries.
- `stop condition`: completion, escalation, or iteration limit.

If compatibility is required, express it in `assertions` with named historical inputs and observable expected outcomes rather than hiding it inside a generic constraint.

Write assertions at the outcome level rather than encoding the intended implementation. For example:

```text
VAL-001: A valid user can sign in and reaches the dashboard.
Evidence: browser flow plus POST /api/auth/login -> 200.
```

Freeze the contract before implementation. Change it only when the user goal, discovered environment facts, or an explicit constraint changes; never weaken it to make the current patch pass.

Keep the contract in the current task context for a short mission. For work spanning many slices or sessions, persist it in the repository's existing planning or state surface rather than inventing a parallel system.

The Mission Contract is a coordination and acceptance artifact. It does not require a code-level contract-test suite. Prove cross-boundary assertions through the real running path by default.

## Milestone Definition

Treat each slice as one milestone: one cohesive, vertically complete outcome that leaves the repository working, maps to one or more mission assertions, can be independently verified, and can be reverted without invalidating unrelated completed milestones.

A milestone is not a layer, a task list, or a time box. Prefer vertical slices that produce user-visible or system-complete value. Frontend, schema, and backend work may belong in one milestone when none of those pieces is useful or verifiable alone.

Use changed non-generated, non-vendored lines only as a soft sizing heuristic, never as the definition:

- Rough target: about 100-500 changed lines.
- Common healthy range: about 300-500 changed lines.
- Over about 800 changed lines: stop and actively review whether the milestone should be split.
- Smaller milestones are preferred when they are the natural independently verifiable unit.
- Larger milestones are acceptable when the change is indivisible and the worker or coordinator can justify why splitting would destroy usefulness or verification value.

Do not pad a milestone to hit a number. Do not split mechanically by file count, layer, or elapsed time.

## Roles

### Coordinator

- Inspect enough of the repository to define the contract and safe boundaries.
- Decompose the goal into the smallest reviewable slice that produces meaningful progress.
- Map every slice to the assertions it claims to satisfy.
- Dispatch agents, adjudicate findings, integrate results, and own final verification.
- Avoid absorbing low-level implementation history that agents can report as artifacts.

### Worker

- Own one bounded implementation slice.
- Treat the slice as one milestone and keep the working tree limited to that milestone's scope.
- Preserve repository patterns and avoid unrelated changes.
- Implement the smallest design that passes the V1 assertions.
- When behavior is testable, write or identify a failing check before implementation.
- Implement until the assigned assertions pass.
- Return changed files, commands and results, artifacts, and unresolved risks.
- Never self-approve the slice.

### Reviewer

- Start independent of the worker's implementation conversation.
- Remain read-only for the reviewed slice; report fixes instead of applying them.
- Review the diff and tests for correctness, maintainability, security, and regression risk.
- Reject mechanisms that cannot pass the complexity admission gate.
- Reject tests that duplicate evidence already supplied by the successful run-through.
- Exercise the resulting behavior as a user or external caller when practical.
- Judge the mission contract, not the worker's explanation of intent.
- Return a clear verdict: `approved`, `needs changes`, or `blocked`.

## Workflow

1. **Frame.** Resolve material ambiguity, define the V1 boundary, and write the mission contract before proposing implementation details.
2. **Slice.** Select one milestone-sized vertical outcome and map it to contract assertions.
3. **Implement.** Give one worker the slice, relevant repository context, write scope, and expected evidence.
4. **Inspect.** Give one independent reviewer the contract, final diff, changed files, and raw verification artifacts.
5. **Validate twice.** Have the reviewer perform both lenses below; do not spawn a second validator by default.
   - **Scrutiny:** inspect implementation quality, tests, trajectory evidence, and integration risks.
   - **User validation:** exercise observable behavior as a black box against the assertions.
6. **Adjudicate.** The coordinator checks whether findings are valid and sends actionable failures back to the same worker as a narrow correction pass.
7. **Repeat.** Re-run the reviewer after material corrections. After three failed review cycles on one slice, the coordinator must re-diagnose or report a concrete blocker rather than adding agents.
8. **Verify.** The coordinator independently runs or inspects the final task-appropriate checks.
9. **Commit.** After reviewer approval and coordinator verification, create exactly one commit for that milestone before starting the next milestone. Follow repository commit conventions. Keep the working tree scoped to that milestone only. Do not create WIP or per-sub-step commits by default. If repository or user policy forbids commits, report the completed milestone instead of violating policy.
10. **Report.** State what changed, what evidence passed, the reviewer verdict, and any residual risk.

## Context Boundaries

Give the worker:

- The goal, current slice, relevant assertions, and write scope.
- The milestone definition, intended vertical outcome, and any sizing or indivisibility note when it matters.
- The V1 boundary and explicit deferred hardening.
- Repository commands, constraints, and patterns required for implementation.
- The expected evidence and report format.

Give the reviewer:

- The goal, non-goals, assertions, and evidence requirements.
- The milestone boundary and why the grouped work forms one independently useful outcome.
- The V1 boundary and the justification for any admitted complexity.
- The final diff or exact changed files.
- Raw command results, screenshots, logs, traces, or runtime artifacts.
- Residual risks as factual claims that still require verification.

Do not give the reviewer:

- The coordinator's preferred verdict.
- The worker's private reasoning, excuses, or persuasive summary.
- Hidden expected findings or a proposed fix.
- Unnecessary conversation history.

## Evidence Order

Prefer the cheapest decisive evidence in this order:

1. Deterministic checks: compile, typecheck, lint, static analysis, schema checks, and focused tests.
2. Outcome checks: integration tests, real API calls, browser flows, screenshots, runtime logs, and deployed smoke tests.
3. Model judgment: code-quality or risk assessment that cannot be made deterministic.
4. Human judgment: product, policy, or irreversible decisions that remain genuinely ambiguous.

A passing command is not sufficient when the assertion is user-visible or integration-dependent. Conversely, do not require a browser, deployment, or external paid call when a deterministic local check fully proves the assertion.

## Verdict Contract

- `approved`: all assigned assertions have adequate evidence; any remaining risk is explicitly non-blocking.
- `needs changes`: at least one finding blocks an assertion or required quality bar, or the patch contains unjustified complexity.
- `blocked`: required evidence or implementation is unavailable because of a concrete external condition.

Reviewer findings must be ordered by severity and include file/line references or reproduction evidence where possible. The coordinator treats the verdict as evidence, not authority.

## Completion Bar

Finish only when:

- The implementation is integrated without unrelated changes.
- Every applicable assertion has evidence or a named reason it could not be checked.
- Reviewer findings are fixed or explicitly accepted as residual risk.
- Every non-trivial mechanism passes the complexity admission gate.
- The coordinator has independently verified the final state.
- The current milestone is approved, verified, and committed, or a no-commit policy is explicitly reported.
- No spawned agent remains active without a purpose.

Use this concise final evidence shape for substantial work:

```text
Changed:
- <files or behavior>

Verified:
- <assertion or command>: <result>

Reviewed:
- reviewer: <identity>, verdict <approved | needs changes | blocked>

Residual risk:
- <none or named risk>
```
