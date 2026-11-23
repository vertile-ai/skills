# Source tools and examples

The review guide is self-contained. These optional resources extend it when the original skills are installed. Resolve each root from the active skill catalog. Set IMPECCABLE_DIR and HALLMARK_DIR to the installed skill roots and TARGET to the source file or directory under review. Run them from the project. Scope Hallmark to app, page, or component according to the target. Use the project's approved browser workflow for live evidence.

```sh
"$IMPECCABLE_DIR/scripts/impeccable" detect --json "$TARGET"
node "$HALLMARK_DIR/scripts/sloplint.mjs" "$TARGET" --scope app --json
```

Read the JSON even when a checker exits nonzero. Findings, invalid input, and an unavailable engine require different conclusions. Confirm suspected issues in context and record which scans actually ran. When a tool is missing, use the review guide and disclose the missing automated coverage.

| Need | Resource relative to the named skill |
| --- | --- |
| Technical audit or experience critique | Impeccable has separate playbooks in `reference/audit.md`, `reference/critique.md`, and `reference/component-review.md`. Its CLI supplies the detector. Its distribution also includes browser helpers, a font index, and specialist agent definitions. |
| Change an existing interface | Impeccable's `reference/distill.md`, `reference/clarify.md`, `reference/adapt.md`, and `reference/polish.md` cover simplification, language, responsive behavior, and final craft. For new work, see `reference/new-work.md` and the operate, read, or persuade mode matching the task. |
| Judge a detector finding | Hallmark's `references/gates.md` distinguishes mechanical, rendered, and judgment-based checks. A style warning needs contextual review. `references/review-hero.md` and `references/review-finish.md` support visual critique. |
| Inspect a worked component | Hallmark's `references/patterns.md` includes HTML, CSS, and JS examples for form errors, control states, a keyboard-operated switcher, and motion. Use `references/interaction-and-states.md` and `references/microinteractions.md` for disclosure behavior. |
| Compare visual directions | Hallmark includes 50 theme previews and their briefs under `references/themes/`, 21 layout studies under `references/macrostructures/`, and four HTML exemplars under `scripts/fixtures/exemplars/`. The theme CLI, photo catalog, capture, and image tools support new designs. Keep the existing project identity during an audit. |
| Select libraries | Hallmark's `references/imagery.md` suggests Lucide, Phosphor, or Heroicons and a consistent family. `references/export-formats.md` shows Tailwind and shadcn/ui token mappings. Use an existing component library and its icons first. The checkers need no UI library added to the application. |
| Edit language | Unslop's `SKILL.md` contains numbered editorial rules and before/after wording. Apply them to visible copy, accessible names, and hidden help. The installed skill contains no separate scripts, fixtures, or reference directory. |

To exercise the static checker on contrasting examples, run these from any project. Inspect the findings in the second example alongside its source.

```sh
node "$HALLMARK_DIR/scripts/sloplint.mjs" "$HALLMARK_DIR/scripts/fixtures/tailwind-pass" --scope component --json
node "$HALLMARK_DIR/scripts/sloplint.mjs" "$HALLMARK_DIR/scripts/fixtures/tailwind-fail" --scope component --json
```
