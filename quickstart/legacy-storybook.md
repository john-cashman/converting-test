---
slug: "/quickstart/legacy-storybook"
title: "Storybook Legacy"
---

import 
  AddSecret,
  Congratulation,
  HelpSection,
  InstallDevDep,
  AddToGitIgnore,
 from "@site/src/partials";

# Legacy Storybook Quickstart

Learn how to setup visual testing in a Storybook using Argos.

To integrate a legacy version of Storybook (\<v8), you have to use [Storycap](https://github.com/reg-viz/storycap) to crawl your Storybook and capture screenshots of your components.

## Prerequisites

To get the most out of this guide, you'll need to:

- [Use Storybook < v8](https://storybook.js.org/docs/get-started/install)
- [Create your project in Argos](https://app.argos-ci.com/new)

{% hint style="info" %}
If use a recent version of Storybook (>v8), follow our [modern Storybook guide](/quickstart/storybook).
{% endhint %}

## 1. Install



## 2. Capture screenshots

There are two ways to capture screenshots of your Storybook:

- If your Storybook is running and accessible via an URL, add this command to your CI pipeline to capture screenshots of your stories:

```sh
# Capture screenshots of your stories
npm exec -- storycap  --outDir ./screenshots
```

- If your Storybook is not deployed, you need to serve your Storybook before capturing the screenshots. Use the following commands:

```sh
# Build Storybook
npm exec -- storybook build --output-dir ./storybook-static

# Screenshot Storybook with Storycap
npm exec -- storycap --serverCmd "npx http-server ./storybook-static --port 6006" http://127.0.0.1:6006/ --outDir ./screenshots
```

Read the [Storycap documentation](https://github.com/reg-viz/storycap) to learn more about the installation and advanced usages.



## 3. Upload screenshots on CI





## Additional resources

- [Argos + Storybook legacy example](https://github.com/argos-ci/argos-javascript/tree/main/examples/storybook-legacy)
- [Storycap documentation](https://github.com/reg-viz/storycap)
- [Storybook documentation](https://storybook.js.org/docs)

---


