# Example report: multilingual contact dialog

This fictional report demonstrates the format. No application was tested to produce it, and the findings are not claims about AZIRAL or a client.

## Scope

A product contact dialog in RU, EN, and KK. The example assumes an authorized local test environment with a simulated submission handler. The same review on a live site would need to account for actual message or record creation.

## Example finding

### P1: the submit action moves outside the keyboard path

- **Trigger:** open the dialog at a narrow width, choose a locale with a long error message, and submit an empty required field.
- **Actual result in this hypothetical case:** the error expands a fixed-height panel; the submit control is clipped, and keyboard focus moves to an element outside the open dialog.
- **Expected result:** the error and submit action stay reachable, and focus follows the dialog's intended interaction.
- **User consequence:** keyboard users cannot correct and complete the contact request through the supported dialog.
- **Location to investigate:** the dialog container's height and overflow, focus management, and error placement.
- **Fix direction:** let content determine height within the viewport, make the relevant region scrollable when needed, and restore the dialog's focus path.
- **Verification to perform:** reproduce the original invalid submission in each affected locale, correct the field, complete the simulated submission, and check focus after closing the dialog.

## Example check plan

| Check | Evidence to capture | Status in this example |
| --- | --- | --- |
| RU/EN/KK longest errors | Error visible with its field and action | Not performed |
| Keyboard completion | Focus sequence, activation, dismissal | Not performed |
| Touch at the dialog edge | Actual tap result and scroll behavior | Not performed |
| Reduced motion | Stable open/close state with meaningful feedback | Not performed |
| Input retention | Entered value after validation and correction | Not performed |

## Delivery note

A real report should replace the hypothetical observations with evidence from the named version and environment. The plan above is not a passed release check.
