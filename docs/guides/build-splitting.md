---
slug: "/build-splitting"
title: "Monorepos"
---


# Monorepos Setup

Optimize visual testing in monorepos with Argos: Use build splitting to manage distinct tests for components and E2E, ensuring precise feedback.

Monorepos, containing multiple packages or applications, can greatly benefit from Argos's build splitting feature. This allows for distinct visual testing builds within the same commit, catering to diverse screenshot categories such as component libraries and end-to-end (E2E) tests.

## Leveraging Build Splitting in Monorepos

Argos supports build splitting across all SDKs, offering a streamlined approach to manage visual tests for different parts of your monorepo. By specifying a unique build name for each category of screenshots, you can isolate and target tests more effectively.

## Practical Application

Imagine your monorepo includes both a component library and an application undergoing E2E testing. You can differentiate these test suites in Argos by assigning a unique `build-name` to each, ensuring clear separation and organization of visual tests. This is achieved by setting the `buildName` option in your Argos integration, as shown in the examples below for both component screenshots and E2E tests:

**For components:**



**For E2E tests with Playwright:**

```ts
// playwright.config.ts

export default defineConfig(
  reporter: [
    process.env.CI ? ["dot"] : ["list"],
    [
      "@argos-ci/playwright/reporter",
      {
        uploadToArgos: !!process.env.CI,
        token: "",
        // highlight-next-line
        buildName: "e2e",
      ,
    ],
  ],
  // Other config
});
```

This approach not only enhances the clarity of your visual testing efforts in a monorepo context but also improves the efficiency of identifying and addressing potential visual regressions across different scopes of your project.
