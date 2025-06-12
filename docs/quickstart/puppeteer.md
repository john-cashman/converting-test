---
slug: "/quickstart/puppeteer"
title: "Puppeteer"
---

import 
  AdditionalResources,
  AddSecret,
  Congratulation,
  HelpSection,
  InstallDevDep,
  ScreenshotGuidesLink,
 from "@site/src/partials";

# Puppeteer Quickstart

Learn how to setup visual testing using the Argos Puppeteer SDK.

## Prerequisites

To get the most out of this guide, you’ll need to:

- [Use Puppeteer](https://pptr.dev/#getting-started)
- Run Puppeteer on your CI/CD
- [Create your project in Argos](https://app.argos-ci.com/new)

## 1. Install



## 2. Take screenshots

Use <code>argosScreenshot</code> helper to capture stable screenshots in your E2E tests.

```js

const puppeteer = require("puppeteer");

(async () => 
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto("http://example.com");
  await argosScreenshot(page, "example.png");
  await browser.close();
)();
```



## 3. Setup your CI





## Additional resources

- [Puppeteer example](https://github.com/argos-ci/argos-javascript/tree/main/examples/puppeteer)
- [Argos Puppeteer SDK reference](/puppeteer)

---


