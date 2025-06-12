---
slug: "/baseline-build"
title: "Baseline build"
---



# Baseline Build

Argos compares screenshots to a chosen **baseline build**, determined by analyzing the commit history of your Git project.

{% hint style="info" %}
This documentation covers Argos' Continuous Integration (CI) mode. For Monitoring mode, refer to the [Monitoring documentation](/monitoring-mode).
{% endhint %}

## What is a baseline build?

A **baseline build** serves as the reference point for comparing screenshots to detect visual changes. Each new build is compared against its corresponding baseline build.

## How does Argos determine the baseline build?

Argos uses your Git commit history to identify the most recent successful build on the **baseline branch** (default branch or custom-configured branch). This build is then set as the baseline for screenshot comparisons.

## What is the baseline branch?

The **baseline branch** is the branch Argos uses as the reference for determining the baseline build:

- For pull request builds, the base branch of the pull request is used.
- For push events, Argos uses the default baseline branch configured in your project.

{% hint style="info" %}
By default, the repository's default branch is used as the baseline branch. You can modify this in the Argos project settings.
{% endhint %}

## Auto-approved branches

Argos supports **auto-approved branches**, where branches matching specified patterns (e.g., `main`, `master`, or `develop`) are automatically approved for comparison.

{% hint style="info" %}
By default, Argos auto-approves your default baseline branch. You can configure auto-approved branches in the Argos project settings.
{% endhint %}

## Configuring branches in project settings

In the project settings, you can configure both the default baseline branch and any auto-approved branches.

<img
  src=projectBranchesSettings
  alt="Project branches settings"
  className="rounded"
/>

## Choose a custom baseline build via SDK

Argos SDKs allow you to specify a custom baseline build if needed. This can be done using:

- `referenceBranch`: The branch name used as the custom baseline.
- `referenceCommit`: The commit hash used to select a specific baseline build.
