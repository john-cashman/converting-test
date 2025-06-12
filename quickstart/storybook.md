---
slug: "/quickstart/storybook"
title: "Storybook"
---

import 
  AddSecret,
  Congratulation,
  HelpSection,
  InstallDevDep,
  AddToGitIgnore,
 from "@site/src/partials";

# Storybook Quickstart

Learn how to setup visual testing in a Storybook using Argos.

## Prerequisites

To get the most out of this guide, you'll need to:

- [Use Storybook v8+](https://storybook.js.org/docs/get-started/install)
- [Create your project in Argos](https://app.argos-ci.com/new)

{% hint style="info" %}
If use a legacy version of Storybook (\<v8), follow our [legacy Storybook quickstart](/quickstart/legacy-storybook).
{% endhint %}

## 1. Install



## 2. Update your package.json

Add the following scripts to your `package.json`:

```json
// package.json

  "scripts": {
    "test-storybook": "NODE_NO_WARNINGS=1 NODE_OPTIONS=--experimental-vm-modules test-storybook"
  
}
```

{% hint style="info" %}
`NODE_OPTIONS=--experimental-vm-modules` is required because Storybook uses Jest that requires this flag to run modern packages like Argos Storybook SDK.
{% endhint %}

## 3. Capture screenshots

Add `.storybook/test-runner.ts` file to your project:

```ts
// .storybook/test-runner.ts


const config: TestRunnerConfig = 
  async postVisit(page, context) {
    await argosScreenshot(page, context);
  ,
};


```

It will capture screenshots of your stories in `./screenshots` directory.



## 4. Setup CI to run tests and upload screenshots

Below is a complete GitHub Actions workflow to build your Storybook, run tests, capture screenshots, and upload them to Argos.
If you use another CI provider, adapt the steps accordingly.

```yml
// .github/workflows/storybook-test.yml
name: Storybook Test

on:
  push:
    branches: [main, master]
  pull_request:
    branches: [main, master]

jobs:
  test:
    runs-on: ubuntu-latest
    timeout-minutes: 30
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4

      - name: Install dependencies
        run: npm ci

      - name: Build Storybook
        run: npm run build-storybook

      - name: Install Playwright dependencies
        run: npx playwright install --with-deps chromium

      - name: Run Storybook tests and capture screenshots
        run: |
          npx concurrently -k -s first -n "SB,TEST" -c "magenta,blue" \
            "npx http-server ./storybook-static --port 6006 --silent" \
            "npx wait-on tcp:127.0.0.1:6006 && npm run test-storybook"

      - name: Upload screenshots to Argos
        # 👇 Replace `` with your project token, available in your Argos project settings.
        run: npm exec -- argos upload --token  ./screenshots
```

To learn how to run tests on a deployed Storybook, refer to the [Storybook test runner documentation](https://storybook.js.org/docs/writing-tests/test-runner#set-up-ci-to-run-tests).



## Additional resources

- [Argos + Storybook example](https://github.com/argos-ci/argos-javascript/tree/main/examples/storybook)
- [Argos Storybook SDK reference](/storybook)
- [Storybook documentation](https://storybook.js.org/docs)
- [Storybook test runner documentation](https://storybook.js.org/docs/writing-tests/test-runner)

---


