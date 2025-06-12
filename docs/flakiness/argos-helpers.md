---
slug: "/argos-helpers"
---

# Argos Helpers

Enhance your visual tests with Argos SDKs: Use `data-visual-test` attributes to manage dynamic content, ensuring consistent, flakiness-free screenshots.

## Helpers

For tailored visual testing, the `data-visual-test` attributes provide control over how elements appear in Argos screenshots. This can be especially useful for obscuring or modifying elements with dynamic content, like dates.

- `[data-visual-test="transparent"]`: Renders the element transparent (`visibility: hidden`).
- `[data-visual-test="removed"]`: Removes the element from view (`display: none`).
- `[data-visual-test="blackout"]`: Masks the element with a blackout effect.
- `[data-visual-test-no-radius]`: Strips the border radius from the element.

**Example: Using a helper attribute to hide a div from the captured screenshot:**

```html
<div id="clock" data-visual-test="transparent">...</div>
```
