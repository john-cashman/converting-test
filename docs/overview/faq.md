---
slug: "/faq"
title: "FAQ"
---

# FAQ

Explore Argos FAQ for insights on team invites, updating baselines, orphan builds, repository sharing, and app permissions for a seamless integration.

## How to invite someone to my Argos team?

Navigate to your team settings, scroll down to members section, and click on "Invite Link". You can now share the team's link with the individuals you want to invite.

{% hint style="info" %}
Everyone has access to Argos public repositories.
{% endhint %}

## How do I update the screenshot comparison baseline?

Argos uses approved builds on base branches as the baseline for comparison. To update the baseline, you need to approve the build on the base branch. You can also defined auto-approved branches in project settings.

## What is an orphan build?

An orphan build means Argos doesn't have a prior set of screenshots to compare with this build. It's totally normal for the first builds.

## Why share repositories with Argos?

Sharing repositories with Argos during installation on GitHub or GitLab is crucial for enabling key features. It allows Argos to access your projects and commit history, which is necessary to find relevant baseline builds for comparison.

## How do I update the repositories list shared with Argos?

After you've set up the Argos app, you can modify the repositories you've allowed Argos to access. Please refer to the relevant section in our detailed [GitHub doc](/github) or [GitLab doc](/gitlab).

## What app permissions does Argos require on Github?

Argos requires the following GitHub app permissions to function:

- **Contents** — used to find a common commit ancestor between branches
- **Statuses** — used to add statuses to commits
- **Pull requests** — used to add comments in pull requests
- **Actions** — used to allow tokenless authentication

We take your security and privacy seriously. If you have any concerns or questions, please don't hesitate to [contact us](/contact-us).
