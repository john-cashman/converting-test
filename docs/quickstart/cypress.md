---
slug: "/quickstart/cypress"
title: "Cypress"
---

import 
  AddToGitIgnore,
  Congratulation,
  HelpSection,
  InstallDevDep,
  ScreenshotGuidesLink,
 from "@site/src/partials";

# Cypress Quickstart

Learn how to setup visual testing using the Argos Cypress SDK.

## Prerequisites

To get the most out of this guide, you’ll need to:

- [Use Cypress](https://docs.cypress.io/guides/getting-started/installing-cypress)
- [Run Cypress on your CI/CD](https://playwright.dev/docs/ci-intro#on-pushpull_request)
- [Create your project in Argos](https://app.argos-ci.com/new)

## 1. Install

Get the Argos Cypress SDK.



## 2. Add `cy.argosScreenshot` command

And add this line to your `cypress/support/e2e.js` file:

```js cypress/support/e2e.js

```

If you use TypeScript, update your `tsconfig.json`:

```js

  "compilerOptions": {
    "types": ["cypress", "@argos-ci/cypress/support"]
  
}
```

## 3. Register Argos in Cypress config

```js cypress.config.js
const  defineConfig  = require("cypress");
const  registerArgosTask  = require("@argos-ci/cypress/task");

module.exports = defineConfig(
  // setupNodeEvents can also be defined in "component"
  e2e: {
    async setupNodeEvents(on, config) {
      registerArgosTask(on, config, {
        // Enable upload to Argos only when it runs on CI.
        uploadToArgos: !!process.env.CI,
        // Set your Argos token (required only if you don't use GitHub Actions).
        token: "",
      );

      // include any other plugin code...
    },
  },
});
```

## 4. Take screenshots

Use <code>argosScreenshot</code> helper to capture stable screenshots in your E2E tests.

```js
// cypress/e2e/homepage.cy.js
it("screenshot homepage", async ( page ) => 
  cy.visit("https://localhost:3000/");
  cy.argosScreenshot("homepage");
);
```





## Additional resources

- [Cypress example](https://github.com/argos-ci/argos-javascript/tree/main/examples/cypress)
- [Argos Cypress SDK reference](/cypress)

---


