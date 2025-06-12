---
slug: "/team-members-and-roles"
title: "Team Members & Roles"
---

# Team Members & Roles

Learn how to manage team members on Argos, and how to assign roles to each member with role-based access control (RBAC).

{% hint style="info" %}
Team roles are available on Pro and Enterprise plans
{% endhint %}

Teams are made up of members, and each member of a team can be assigned a role. These roles define what you can and cannot do within a team on Argos.

As your project scales and you add more team members, you can assign them roles to ensure that they have the right permissions to work on your projects.

## Access Roles Overview

Argos distinguishes between different roles to help manage team members' access levels and permissions. These roles are categorized into two groups: team level and project level roles. Team level roles are applicable to the entire team, affecting all projects within that team. Project level roles are confined to individual projects.

![Team and project roles relationship diagram](./team-members-and-roles/permissions-diagram.png)

The two groups are further divided into specific roles, each with its own set of permissions and responsibilities. These roles are designed to provide a balance between autonomy and security, ensuring that team members have the access they need to perform their tasks while maintaining the integrity of the team and its resources.

- [Team level roles](#team-level-roles): Users who have access to all projects within a team
  - [Owner](#owner-role)
  - [Member](#member-role)
  - [Contributor](#contributor-role)
- [Project level roles](#project-level-roles): Users who have restricted access at the project level. Only contributors can have configurable project roles
  - [Project Administrator](#project-administrator)
  - [Project Reviewer](#project-reviewer)
  - [Project Viewer](#project-reviewer)

## Team level roles

{% hint style="info" %}
Team level roles are available on Pro and Enterprise plans
{% endhint %}

Team level roles are designed to provide a broad level of control and access to the team as a whole. These roles are assigned to individuals and apply to all projects within the team, ensuring centralized control and access while upholding the team's security and integrity.

- **[Owner](#owner-role)** and **[Member](#member-role)**: Have the highest level of control. They can manage, modify, and oversee the team's settings, and all projects
- **[Contributor](#contributor-role)**: A unique role that can be configured to have any of the project level roles or none. If a contributor has no assigned project role, they won't be able to access that specific project. Only contributors can have configurable project roles

### Owner role

{% hint style="info" %}
The owner role is available on Pro and Enterprise plans
{% endhint %}

The owner role is the highest level of authority within a team, possessing comprehensive access and control over all team and project settings.

#### Key responsibilities

- Oversee and manage all team resources and projects
- Modify team settings, including billing
- Grant or revoke access to team projects and determine project-specific roles for members
- Access and modify all projects, including their settings

#### Access and permissions

Owners have unrestricted access to all team functionalities, can modify all settings, and change other members' roles.

Team owners inherently act as project administrators for every project within the team, ensuring that they can manage individual projects' settings and deployments.

#### Additional information

Teams can have more than one owner. For continuity, we recommend that at least two individuals have owner permissions. Additional owners can be added without any impact on existing ownership. Keep in mind that role changes, including assignment and revocation of team member roles, are an exclusive capability of those with the owner role.

### Member role

{% hint style="info" %}
The member role is available on Pro and Enterprise plans
{% endhint %}

Members are the most common role in the team. They have access to all projects but do not have access to team management settings.

#### Key responsibilities

- See and review builds
- Access and modify all projects, including their settings

#### Access and permissions

Members have full autonomy to review projects or edit settings. However they can't edit team settings or invite new users to the team, only owners can.

### Contributor role

{% hint style="info" %}
The contributor role is available on Enterprise plans
{% endhint %}

Contributors offer flexibility in access control at the project level. To limit team members' access at the project level, they must first be assigned the contributor role. Only after being assigned the contributor role can they receive project-level roles. **Contributors have no access to projects unless explicitly assigned.**

Contributors may have project-specific role assignments, with the potential for comprehensive control over assigned projects only.

#### Key responsibilities

- Typically assigned to specific projects based on expertise and needs
- Review builds and edit project settings — _Depending on their assigned [project role](#project-level-roles)_

#### Access and permissions

Contributors can be assigned to specific projects and have the same permissions as [project administrators](#project-administrator), [project reviewers](#project-reviewer), or [project viewers](#project-viewer). They can also be assigned no project role, which means they won't be able to access that specific project.

See the [Project level roles](#project-level-roles) section for more information on project roles.

## Project level roles

{% hint style="info" %}
Project level roles are available on Enterprise plans
{% endhint %}

Project level roles provide fine-grained control and access to specific projects within a team. These roles are assigned to individuals and are restricted to the projects they're assigned to, allowing for precise access control while preserving the overarching security and integrity of the team.

- **[Project Administrator](#project-administrator)**: Team owners and members inherently act as project administrators for every project. Project administrators can review builds, manage all project settings, and manage production environment variables
- **[Project Reviewer](#project-reviewer)**: Can review builds.
- **[Project Viewer](#project-viewer)**: Has read-only access to a specific project.

### Project Administrator

{% hint style="info" %}
The project administrator role is available on Enterprise plans
{% endhint %}

Project reviewers play a key role in working on projects, mirroring the functions of team members, but with a narrowed project focus.

#### Key responsibilities

- Review builds

### Project Reviewer

{% hint style="info" %}
The project reviewer role is available on Enterprise plans
{% endhint %}

Project administrators hold significant authority at the project level, operating as the project-level counterparts to team members and owners.

#### Key responsibilities

- Review builds
- Govern project settings
- Add contributors to project

#### Access and permission

Their authority doesn't extend across all projects within the team. Project administrators are restricted to the projects they're assigned to.

### Project Viewer

{% hint style="info" %}
The project viewer role is available on Enterprise plans
{% endhint %}

Adopting an observational role within the project scope, they ensure transparency and understanding across projects.

#### Key responsibilities

- View and inspect all builds and screenshots

## Default Project Roles

When you set a default role in a specific project, all of your team’s contributors will automatically inherit that default role when they’re granted access to that project. This feature helps you streamline role management and maintain consistent permissions for new contributors.

**To set a default role in a project:**

1. Navigate to the project's **Settings** page.
2. Scroll down to the **Access management** section.
3. Click on **Set default contributor level**.
4. Select the desired default role (Viewer, Reviewer, or Admin).
5. Click **Save**.

After setting this default, every team member with a role "contributor" will have access to this project with this default role. You can still override this by assigning a custom role to individual contributors later.

This approach simplifies onboarding, helps ensure consistent access levels, and reduces the time spent manually configuring roles.
