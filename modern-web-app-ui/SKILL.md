---
name: modern-web-app-ui
description: Design, refine, or audit web app screens for visual hierarchy, icon-first actions, concise copy, and progressive disclosure across pointer, keyboard, and touch.
---

# Modern Web App UI

Start with the task someone came to do. Identify what they need to recognize, decide, and act on before touching the screen. Look for established interaction patterns, visual conventions, and any design system the product already uses. Give the primary task the strongest visual weight through placement, spacing, type, and contrast.

## Choose what the user sees

- Show the thing itself when recognition is faster than reading. Use an actual product screenshot for a feature preview, a thumbnail for a visual item, or a diagram for a spatial relationship. Preserve meaningful alternatives for informative images. Decorative imagery should stay silent to assistive technology.
- Prefer an icon-only button when the action is recognizable in its immediate context. A magnifying glass beside a query field can run a search. Give the button the accessible name "Search", hide the decorative glyph from screen readers, and expose the same wording on hover and keyboard focus. Use the same icon for the same action throughout the app.
- Test recognition before hiding a label. If an arrow could mean continue, send, or open, keep a short visible verb that names the actual outcome. Give interactive icons a visible focus state and a comfortable touch target.
- Read each line of interface copy as a user. Keep it if it supplies a fact, decision, action, or recovery step. Cut generic encouragement, repeated instructions, decorative badges, inflated claims, and captions that merely describe the obvious. Use the product's real terms and direct verbs. Keep the content people came to read, compare, or edit visible while they work.

## Place useful information at the shallowest level it needs

| Level | What belongs here | Interaction |
| --- | --- | --- |
| 1. Visible | The task, relevant content, current state, primary action, blocking error, and any consequence needed before acting. | Immediately legible at the shipped viewport. |
| 2. Hover or focus | A short action name, shortcut, unit definition, or one-line clarification. | Anchor a tooltip to its trigger. Show it on keyboard focus as well as hover. Allow Escape to dismiss it. |
| 3. Click or tap | Optional controls, history, or detail people deliberately choose to inspect. | Use a named disclosure, popover, or drawer beside the item it explains. Support keyboard activation and predictable focus when it closes. |

Prefer the deeper level whenever it preserves the task. Remove useless copy entirely. On touch, expose useful hover detail through a tappable information control or alongside related expanded detail. A tap on an action button should perform its advertised action. Keep interactive content out of tooltips.

Choose the level for the current task. A timestamp may belong in expanded details while someone browses items, and directly in each row when they compare items by recency. Use only the levels the interaction needs.

## Review in context

Use the [review guide](references/review.md) for a critique, a technical audit, or a copy edit. For a full review, use all three passes. For source detectors, executable examples, visual references, and UI library choices, consult the [resource guide](references/resources.md).

For a full audit, inventory the user-facing surfaces and routes, including role-specific views and shared controls. Follow their primary tasks in the rendered product. Compare desktop and touch layouts, supported themes, and relevant loading, empty, error, and success states. Use the project's browser workflow. Check contrast, keyboard focus, icon names, and whether a touch user can retrieve each useful hidden detail.

Report findings in impact order. For each, name the screen and state, describe the observed friction, and give the smallest concrete change. When excess text is the issue, quote it and specify the replacement icon, disclosure level, or deletion. Group repeated issues under their shared component and list affected surfaces. State which screens were inspected live, which were reviewed in source only, and which remain unverified. For implementation requests, apply the scoped changes and verify the resulting interaction at the sizes it ships at.
