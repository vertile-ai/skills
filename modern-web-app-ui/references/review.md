# Reviewing a web app

## Critique the rendered experience

Look at the product before reading detector output. Pick the primary task for each audience. A work screen earns its density through useful controls and comparable values. A reading screen earns its space through comfortable measure, legible notation, and clear section breaks. A public page should show the actual product, result, or material behind its claim. Preserve the supplied brand, facts, and intended tone.

At the actual viewport, identify what draws the eye first, what action it suggests, and what competes with it. Walk the task as a newcomer and a returning user. Check whether the subject is recognizable, the reading order survives narrow widths, and repeated components mean the same thing everywhere. On a new page, choose its composition from the audience, task, and available material. Generic card grids, decorative gradients, repeated eyebrows, and oversized heroes are leads to investigate. Record a concrete effect before calling one a defect.

## Audit the implementation

Use the source scans in the resource guide when available. Check the following dimensions against the running product and the project's own contracts.

| Dimension | What to verify |
| --- | --- |
| Accessibility | Complete the primary flow with a keyboard. Inspect names, landmarks, focus order, contrast, error association, reduced motion, and focus restoration. Confirm ambiguous icons with their surrounding content visible. |
| Performance | Follow the affected interaction. Look for layout shifts, oversized image transfers, or motion that stutters. Use measurements when claiming a performance regression. |
| Theming | Compare supported themes, including focus, selected, disabled, and error states. Trace drift back to the relevant token or component. |
| Responsive behavior | Check narrow and wide layouts, text enlargement, overflow, and touch access to hidden information. Exercise touch gestures when relevant and record the input actually used. |
| Implementation integrity | Verify that actions work, form values survive correctable errors, and loading, empty, success, and failure states communicate what happened. Compare rendered behavior with the product's design system. |

## Edit the copy

Read controls in their actual state. Use one name for each concept and a direct verb for each action. Remove unsupported claims, jargon, filler, and repeated instructions. Preserve domain terms, numbers, units, and the facts needed to recover from errors. Check image, icon, deletion, or deeper disclosure against the decision the user has to make.

- A search icon followed by “Search” and “Use the search bar to search” needs a labeled input. Remove the repeated instruction.
- Replace “Something went wrong” with “Enter a date after 12 May” only when that is the actual validation rule. Keep it beside the field.
- Before a consequential action, state its scope. “Delete 4 items” tells the user what the next click affects.

## Triage and recheck

Record the route, viewport, role, state, and evidence that expose the problem. Use P0 for a blocked primary task, P1 for substantial access or usability loss, P2 for friction with a workable alternative, and P3 for polish. Separate reproducible failures from suspected issues. Treat house-style warnings as prompts for judgment. If two tools flag a shared token and eight routes inherit it, report one finding with the affected routes and the evidence from each tool. Keep unrelated failures distinct even when they appear on the same control.

For example, if a status explanation opens only on mouse hover, verify keyboard focus and touch before reporting it. Quote the missing information, identify the shared status component, describe the affected audience, and specify how to retrieve it on each input. After an authorized fix, repeat the same interaction and scan, then check one other consumer of the component. For a review-only request, deliver the findings and identify the checks needed to verify a future fix.
