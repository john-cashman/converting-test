---
slug: "/quickstart/webdriverio"
title: "WebdriverIO"
---

import 
  AddSecret,
  Congratulation,
  HelpSection,
  InstallDevDep,
  ScreenshotGuidesLink,
 from "@site/src/partials";

# WebdriverIO Quickstart

Learn how to setup visual testing using the Argos WebdriverIO SDK.

## Prerequisites

To get the most out of this guide, you’ll need to:

- [Use WebdriverIO](https://webdriver.io/)
- Run WebdriverIO on your CI/CD
- [Create your project in Argos](https://app.argos-ci.com/new)

## 1. Install



## 2. Take screenshots

Use <code>argosScreenshot</code> helper to capture screenshots in your E2E tests.

```js


describe("Integration test with visual testing", () => 
  it("covers homepage", async () => {
    await browser.url("http://localhost:3000");
    await argosScreenshot(browser, "homepage");
  );
});
```

Screenshots are stored in `screenshots/argos`, don't forget to add this folder to your `.gitignore`.

## 3. Setup your CI





## Additional resources

- [Argos WebdriverIO SDK reference](/webdriverio)

---


