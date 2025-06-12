---
slug: "/argos-cli"
title: "Command Line"
---


# Argos Command Line Interface (CLI)

Use the Argos CLI for seamless screenshot uploads to our visual testing platform, ideally integrated into your CI workflow.

You can access `@argos-ci/cli` through our [npm package](https://www.npmjs.com/package/@argos-ci/cli). The source code is available on our [GitHub repository](https://github.com/argos-ci/argos-javascript/tree/main/packages/cli).

## Installation



## Configuration

Your configuration requirements may vary depending on the CI you use. Typically, you'll need to set ARGOS_TOKEN as a environment variable (ie. secret).

{% hint style="info" %}
You can also specify the token with the `--token=<your-repository-token>` argument. However, for security reasons, we recommend using an environment variable instead.
{% endhint %}

## Upload Command

Use the `upload` command to upload screenshots stored in your `./screenshots` directory.



### Debug mode

You can enable debug mode by setting the `DEBUG` environment variable.



## Help Command

To view a list of available options, use the argos help command.


