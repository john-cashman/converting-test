---
slug: "/wait-for-loading"
---

# Wait for Loading

Master timing in visual tests with Argos: Use `aria-busy` to ensure screenshots are captured post full page load, enhancing accuracy and consistency.

## Usage

`argosScreenshot()` delays capturing screenshots until no elements with `aria-busy` are detected, ensuring full page load.

```jsx

```

**We recommend to apply `aria-busy` on your loader components be ensure that your page is fully loaded before a screenshot is taken.**
