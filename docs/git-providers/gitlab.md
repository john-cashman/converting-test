---
slug: "/gitlab"
title: "GitLab"
---

# Integrating Argos with GitLab

Enhance your GitLab workflow with Argos for streamlined visual testing, direct feedback on merge requests, and easy GitLab repository access.

## Advantages of GitLab Integration

- Log in effortlessly via GitLab
- Access to GitLab repositories
- Get Argos feedback on your pull requests.

## Connecting a GitLab Repository

By leveraging GitLab's Personal Access Token, Argos communicates via a dedicated GitLab Bot User. This setup ensures direct feedback on your pull requests.

#### 1. Generate a Personal Access Token in GitLab

- Go to [GitLab tokens settings](https://gitlab.com/-/profile/personal_access_tokens?name=argos2&scopes=api,read_user).
- Click "Add new token".
- Set an expiration date 12 months ahead (maximum allowed).
- Click "Create personal access token" and then copy the generated token.

![Generate a Personal Access Token in GitLab](@site/src/img/gitlab-create-token.png)

{% hint style="info" %}
You can also use a [Project Access Token](https://docs.gitlab.com/ee/user/project/settings/project_access_tokens.html) if you want to restrict access to a single project. If you choose this option, be sure to use set the role of the token as **developer**.
{% endhint %}

#### 2. Configure the Generated Token in Argos

On Argos, navigate to "Team Settings" → "GitLab", enter the generated token and save the changes.

![Configure GitLab in Argos](@site/src/img/gitlab-configuration-argos.png)

#### 3. Link GitLab Project to Argos

In Argos, go to "Team projects", then click on "Create a new Project". Select "Continue with GitLab", pick your GitLab organization and the desired repository. The new project will appear in your projects list.

![Configure GitLab in Argos](@site/src/img/argos-create-new-project.png)

## Connecting a Argos project to a GitLab Repository

First, ensure the [GitLab Personal Access Token has been configured correctly](#connecting-a-gitlab-repository)

In Argos, navigate to "Project Settings" → "Connect Git Repository" and select the desired GitHub repository for association.
