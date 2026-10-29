---
name: aziral-ui-release
description: Review a frontend before release with reproducible findings for multilingual layout, touch, keyboard, forms, and motion. Use for scoped UI release checks and fix verification; do not treat an opinion about styling as a demonstrated defect.
---

# AZIRAL UI Release Review

Produce an actionable record of the interface a person can use. This original AZIRAL workflow is independent of Paul Bakaus's Impeccable. It works without that engine or detector; existing detector results can support the review when relevant.

## Bound the review

Identify the target route or component, version, requested locales, intended devices, and the primary completion path. Determine whether the user requested review only or also fixes. Preserve unrelated pages and the incumbent design unless redesign is part of the task.

Read the relevant implementation, translations, and existing checks. Run the interface when possible. If the app or a required service cannot run, inspect available artifacts and record the resulting limits rather than claiming a passed interaction.

Choose scenarios by consequence. A contact form needs submission and failure checks; an interactive hero needs gesture and scroll checks; a navigation change needs routes, focus, and menu dismissal. Do not force every surface through an unrelated checklist.

## Inspect languages and layouts

When RU, EN, or KK is in scope, inspect the actual strings in each required locale. Include long navigation labels, validation errors, names, prices, and dates used on the target surface. Check the corresponding language route and preserve locale through the completion path where intended.

For Kazakh, verify that the font renders `Ә Ғ Қ Ң Ө Ұ Ү Һ І` and lowercase equivalents. Identify missing or fallback content separately from layout defects. Do not certify translation quality from visual fit alone.

Use the product's target dimensions. A narrow phone, a medium layout, and a desktop view are useful starting points when responsive behavior changes. Record CSS pixels and any zoom, orientation, or emulation settings that affect the finding.

## Reproduce actions through the available inputs

Use the browser or device tools permitted by the host. Examine the user path, not only the initial screenshot.

- **Touch and pointer:** activate the intended control, inspect overlapping hit areas, scroll through interactive regions, and cancel a drag where relevant. State whether the evidence comes from real touch, emulation, or a desktop pointer.
- **Keyboard:** follow the focus path through the target, activate controls, open and dismiss menus or dialogs, and confirm a visible focus indicator. Check that a hover-dependent action has an equivalent path.
- **Forms:** inspect labels and required fields, try invalid input, correct it, and verify that useful input survives validation. Check loading and repeated submission behavior. Exercise success or service failure only within the authorized environment; use an existing test mode when available.
- **Motion:** check the reduced-motion state and whether movement destabilizes controls, hides information, or obstructs reading. A still state should preserve the action and meaning.

A live form can send mail, create records, or make a purchase. Review its consequences before exercising submission. Existing authorization determines whether that action is in scope; a UI review alone does not authorize external messages or financial actions.

## Write findings that can be acted on

For each finding, include the trigger, observed behavior, expected behavior, user consequence, location, and useful evidence. A screenshot proves a visual condition; it does not prove that a request completed or that stored data is correct.

Rank by observed consequence:

| Priority | Meaning |
| --- | --- |
| P0 | A release blocker with demonstrated severe harm or broad inability to complete the primary task |
| P1 | A primary action is blocked for a supported language, input method, or device |
| P2 | A recoverable error, misleading state, or meaningful usability obstacle |
| P3 | A visual or wording refinement with limited task impact |

Adjust priority to the actual reach and available workaround. Keep an untested concern labelled as a question to investigate. Do not inflate the count by reporting the same root cause once per locale.

Use [the review template](references/review-template.md) for the record. Include successful checks only when they were actually performed. Distinguish a confirmed failure from unavailable evidence.

## Verify fixes and conclude

If fixes are authorized, change the smallest appropriate source area and retest the original failure. Check nearby behavior that the change could affect. Use existing meaningful tests when the implementation or release policy calls for them; a review-only task does not require a new CI system.

Finish with the important findings, fixes if any, tested version and environments, and remaining limits. State release readiness only for the reviewed scope. A passed browser walkthrough is not a blanket security, accessibility, performance, or translation certification.
