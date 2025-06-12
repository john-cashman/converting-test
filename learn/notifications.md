---
slug: "/notifications"
title: "Notifications & Alerts"
---


# Notifications & Alerts

Stay informed with Argos: Get build results directly in your GitHub pull requests for a streamlined review process and efficient change management.

## Pull request comment overview

Every time there's an update to a build status, Argos automatically comment to the associated pull request thread. This comment contains the latest build status, together with a convenient link that leads you directly to the detailed build page on Argos.

<img
  src=githubPrComment
  alt="Argos GitHub pull request comment"
  className="rounded"
  style={ marginBottom: 20, width: 600 }
/>

## Silence pull request Comments

If you would like to stop automatic comments from appearing on your pull request by the Argos GitHub bot, you can silence them through the project Settings:

1. Go to your project Settings in Argos.
2. In the "Connected Git Repository" section, you will find a checkbox for "Enable pull request comments".
3. Uncheck this box to disable the feature and save the settings.

Once you uncheck the box, Argos will stop posting build status updates in your pull requests. You can always re-enable it by checking the box again.
