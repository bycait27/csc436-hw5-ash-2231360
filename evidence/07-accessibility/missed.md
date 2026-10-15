# Scanner-Missed Defect

**Symptom:** When a keyboard-only user triggers a failed action (such as attempting to close a ticket that results in an API error), the error message appears on the screen, but the browser focus remains trapped on the submit/action button. Because the error renders above the current viewport or outside the user's active line of sight, the user perceives the app as "doing nothing" and must manually tab backward to discover the error.

**Mechanism:** The application updates component state to render an error banner, but fails to programmatically shift focus (`element.focus()`) to the error container or use an ARIA live region (`role="alert"`) to signal the failure to assistive technologies.

**Who is Impacted:** Keyboard-only sighted users (who miss the visual cue because it's scrolled out of view) and screen reader users (who receive no audio announcement of the failure).

**The Fix:**

1. Add `role="alert"` and `tabIndex={-1}` to the error container.

2. Programmatically call `.focus()` on the error container when a mutation error is caught so the user's focus (and screen reader context) is immediately directed to the failure message.

3. Ensure `scrollIntoView({ behavior: 'smooth' })` is invoked on the error element if it renders above the fold.