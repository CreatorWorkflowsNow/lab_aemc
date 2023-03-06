---
layout: default
title: App Engine
parent: 1 | Configure
nav_order: 120
---

# App Engine
{: .no_toc }

[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## App Engine Studio Guided Setup

Navigate to **App Engine Studio \Configuration \Guided Setup** in your development instance to access the App Engine Studio Guided Setup.

![](../images/2023-03-03-16-37-59.png)

{: .warning}
Be sure your application scope to 'App Engine Studio'. If not, use the application picker to change the current session's scope

![](../images/2023-03-03-16-39-04.png)

## Review and set up tooling in the development instance

Review and update App Engine Studio developer access to builder tools during development.

## Review Flow Designer access settings from App Engine Studio in development

Review and update App Engine Studio developer access settings to Flow Designer Resources and update as necessary.

Developers can leverage Flow Designer capabilities while creating logic and automation for custom applications.

Consider restricting developer access to Flow Designer Resources using content filtering for Flow Designer. This allows administrators to manage access to Flow Designer resources and specify which features App Engine Studio users can leverage while building applications.

![](../images/2023-03-03-16-41-01.png)

*This step is not required as part of the initial application setup.*

Flow Designer access from App Engine Studio can be updated later to provide developers the editing capabilities that best suit their experience and needs.

*For more information on Flow Designer resources, see [[Product Documentation: Content Filtering for Flow Designer]](https://docs.servicenow.com/csh?topicname=content-filtering-flow-designer.html)*

## Review Service Catalog access settings in development

Review App Engine Studio developer access to the Catalog Builder tool's catalog item templates and catalogs / categories, and update access as necessary.

By default, App Engine Studio developers can leverage catalog templates to quickly create record producers or catalog items. Developers can also publish catalog items to any catalog. If you wish to limit access to templates or restrict publishing access to catalogs or categories, update the access accordingly in Catalog Builder.

![](../images/2023-03-03-16-42-14.png)

*This step is not required as part of the initial application setup.*

Catalog access from App Engine Studio can be updated at a later point to modify developer access to App Engine Studio catalogs, categories, and catalog templates.

*For more information on creating or editing catalog items, see
[[Product Documentation: Catalog Builder]](https://docs.servicenow.com/csh?topicname=catalog-builder.html)*

## Configure Instance Scan definitions

Deploy custom applications with confidence by setting up Instance Scan definitions to monitor instance health throughout the deployment process. Instance scans interrogate your instance for configurations and health issues, allowing administrators an opportunity to address best practices and to avoid similar configuration issues in the future.

Instance Scan definitions are executed automatically when App Engine Studio applications are promoted to the **Testing** instance. Instance Scan results will be logged in the Notes section of the Deployment Request record.

The App Engine Studio application does not ship with any out-of-box Instance Scan definitions (however a few Instance Scan definitions are installed with the Deployment Pipeline plugin to run basic performance checks).

Work with professional ServiceNow developers to configure Instance Scan definitions and enforce best practices in your environments.

![](../images/2023-03-03-16-42-38.png)

**Enable and configure Instance Scan properties in your production instance if you plan to clone!**

*For more information on managing instance health scans, see [[Product Documentation: Instance Scan]](https://docs.servicenow.com/csh?topicname=hs-landing-page.html)*

## Set up user access

Configure the admin group and other general settings for App Engine Studio users.

## Set up administrator group in development

Configure App Engine Studio administrator group membership in the [development] instance to manage development activities that occur in the development environment.

![](../images/2023-03-03-16-42-55.png)

While development activities will be managed in the [development] instance, administrators manage application intake, collaboration, and deployment requests in [production].

Group membership does not sync across instances; therefore, system administrators are required to add users in both the development and production instances.

{: .note}
Group membership does not sync across instances, therefore App Engine Studio administrator group membership will also need to be provisioned in the [production] instance as part of the Pipelines and Deployment or Application Intake Guided Setup activities*

b.  **Grant access to current developers in development**

Allow existing application developers who are already assigned the **delegated_developer** role access to the App Engine Studio application by adding them to the 'App Engine Studio Users' assignment group.

***Note:** If you wish to grant multiple developers access at one time, advance to the next step to manage access more efficiently*

c.  **Grant access to other users in development**

After provisioning access for existing developers, grant App Engine Studio access to other users within the organization by adding them to the 'App Engine Studio Users' group.

![](../images/2023-03-03-16-43-47.png)

[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

[PREVIOUS]: ../110_Configure_Overview
[NEXT]: ../130_Pipeline_and_Deployment