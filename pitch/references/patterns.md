# Pitch Patterns

Use these patterns to adapt the same verified selling point across formats. Do not copy claims from examples into user work.

## Research Anchors

- [GitHub Docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes) says a README should tell people why the project is useful, what it does, how to get started, where to get help, and who maintains it.
- [Y Combinator](https://www.ycombinator.com/blog/how-to-pitch-your-company/) pitching guidance emphasizes clarity and concision, starting with what the company does.
- [Sequoia](https://sequoiacap.com/article/writing-a-business-plan/) starts with a single declarative company purpose, then problem, solution, why now, market, competition, model, team, financials, and vision.
- [Google Ads Help](https://support.google.com/google-ads/answer/14783551) emphasizes attention, branding, connection, and direction; it recommends getting to the story quickly, keeping the message focused, and using a clear CTA.
- [Google's ABCD playbook](https://www.thinkwithgoogle.com/_qs/documents/8472/ABCD_Complete_V7b_HR_1.pdf) recommends introducing the product or brand in the first five seconds and using tight framing, memorable imagery, pacing, and specific calls to action.

## Universal Hook Shapes

Use one of these when the user has supplied the facts:

```text
For [audience], [product/project] turns [painful current state] into [better outcome] by [differentiator].
```

```text
[Audience] no longer has to [pain]. [Product/project] helps them [outcome] with [proof/differentiator].
```

```text
[Specific proof] shows [product/project] can [valuable outcome] for [audience].
```

```text
The fastest way to understand [product/project]: [one concrete result it creates].
```

## README Pattern

Goal: make a visitor understand usefulness before setup details.

Recommended order:

1. Name plus value-led one-liner.
2. One short paragraph: audience, pain, outcome, differentiator.
3. Visual proof if available: screenshot, demo GIF, CLI output, benchmark, example result.
4. "Why use this" bullets tied to outcomes, not generic features.
5. Quick start with minimal commands.
6. Example workflow.
7. Configuration/API/reference links.
8. Help, contribution, license, maintainers.

Opening template:

```markdown
# [Project]

[Project] helps [audience] [outcome] without [pain/tradeoff].

It does this by [differentiator], so [specific practical benefit]. [Proof if supplied].
```

Feature bullets should use this shape:

```markdown
- [Outcome]: [how the project creates it].
```

Avoid:

- Starting with installation before value.
- Long architecture explanations before use cases.
- Feature nouns with no user outcome.
- Claims like "simple" or "powerful" without evidence.

## Short Video Script Pattern

Goal: earn attention in 3-5 seconds, then prove the claim.

Recommended order:

1. 0-5s hook: audience, pain/outcome, product/subject visible or named.
2. 5-12s proof: demo moment, before/after, credible detail, or concrete example.
3. 12-25s explanation: one mechanism, not a feature tour.
4. Final CTA: one action.

Script template:

```text
[0-5s] [Audience] can now [outcome] without [pain]. Here is [product/project] doing it.
[5-12s] Watch [specific proof/demo].
[12-25s] The key is [differentiator/mechanism].
[CTA] [Specific next action].
```

Avoid:

- Host intros before value.
- Logos or atmosphere before the reason to watch.
- Multiple unrelated benefits in one short script.
- Unsupported urgency.

## Presentation Pitch Pattern

Goal: make the audience understand the opportunity and remember the strongest proof.

Recommended order:

1. Title: company/project plus one-sentence purpose.
2. Problem: the painful current state for a specific audience.
3. Solution: the eureka moment and value proposition.
4. Why now: timing or constraint that makes this relevant.
5. Proof: traction, demo, metric, customer evidence, benchmark, or shipped artifact.
6. Differentiation: why alternatives fall short.
7. Ask: what decision or next step is requested.

Slide-title style:

```text
[Audience] needs [outcome], but [current blocker]
[Project] removes [blocker] by [differentiator]
[Proof] shows this is already working
```

Avoid:

- Section labels that do not carry meaning, such as only "Problem" or "Solution".
- Investor-style market claims unless the user supplied the market evidence.
- Ending without a concrete ask.

## Rewrite Pass

After drafting, tighten in this order:

1. Move the strongest real selling point earlier.
2. Replace abstract adjectives with concrete outcomes.
3. Delete unsupported claims.
4. Shorten the hook until it can be understood in one breath.
5. Add a direct CTA.
