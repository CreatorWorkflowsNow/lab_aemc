---
layout: default
title: Sys Admin Guide Import
nav_order: 999
---

ServiceNow App Engine Governance Lab
{: .fs-10 }
{: .no_toc }

{: .note }
The following content is certified for the Tokyo release of ServiceNow.

{: .highlight }
The content in this guide applies to App Engine Studio v22.0.3.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# App Engine Studio Overview {#app-engine-studio-overview}

App Engine, powered by the Now Platform, fuels rapid delivery of Creator Workflows with great experiences for everyone. With more people building with less complexity, App Engine allows developers to create low-code apps fast, and safely scale cross-enterprise experiences that users love.

App Engine Studio is available with App Engine and is designed from the ground up to address low-code development needs. App Engine Studio enables professional developers, line of business technologists (citizen developers), and low-code developers to build applications individually or in collaborative teams on the same platform, resulting in faster time to value and better applications that scale without sprawl.

With guidance-driven development flows and pre-configured application templates, developers across the enterprise can build and deliver apps quickly. Developers can leverage many out-of-box components available through drag-and-drop interfaces to create fulfilling user experiences that are critical to end-user adoption.

Administrators control which applications to deploy by reviewing and testing applications created by App Engine Studio developers -- and by delegating development to business units in your organization, administrators are freed up to address more strategic, system-wide issues.

![](/images/image2.jpeg)
 
*\* App Engine Studio application templates are not captured in update sets, however modifications to templates will be captured*

App Engine Studio is the ideal ServiceNow development environment for no-code and low- code application development for developers of all skill levels. Pro-code developers can use App Engine Studio as a starting point for application development and easily transfer their applications to ServiceNow Studio when advanced configurations are necessary.

Since development is supported between the two environments, low-code and pro-code developers can easily collaborate to deliver custom applications.

All configurations to an application, whether performed in App Engine Studio or ServiceNow Studio, can be captured in the same private application scope. Application artifacts configured in App Engine Studio can also be managed in ServiceNow Studio. However, some application artifacts can only be accessed and configured in ServiceNow Studio. These include business rules, notifications, and service portal pages.

[Back to top](#top){: .btn .btn-purple }

---
# Personas and Roles {#personas-and-roles}

System Administrator
{: .fs-6 }

**Responsibilities**
-   Install and configure App Engine Studio and dependencies
-   Define Environments and configure Pipelines
-   Provision App Engine Studio administrator group access
-   Upgrade the App Engine Studio application, when applicable
-   Define guardrails for which App Engine Studio Administrators can
    approve or reject application intake requests
-   Collaborate with professional ServiceNow developers to create
    Instance Scan definitions for the platform
-   Collaborate with App Engine Studio Administrator(s) to resolve
    application conflicts that arise on the platform

**Role required**
- admin

App Engine Studio Administrator
{: .fs-6 }

**Responsibilities**

-   Manage App Engine Studio processes and properties
-   Review and approve / reject submitted application requests, based on
    intake guardrails defined by System Administrator
-   Provision App Engine Studio user access
-   Review submitted App Engine Studio applications
-   Manage Deployment Requests
-   Manage promotion of App Engine Studio applications across instances
-   Execute ATF tests / suites in testing instance
-   Ensure Instance Scan is run with proper definitions
-   Collaborate with System Administrator to resolve application
    conflicts that arise on the platform

**Role(s) required**

-   sn_app_eng_studio.admin
-   atf_test_designer
-   scan_admin

Professional ServiceNow Developer
{: .fs-6 }

**Responsibilities**

-   Build and test applications in ServiceNow Studio and App Engine
    Studio
-   Collaborate with citizen developers, on an as-needed basis, to
    deliver applications in App Engine Studio, including:
    -   Ensure application development and organizational best practices
        are followed by citizen developers
    -   Assist in review and testing of submitted App Engine Studio
        applications
-   Build complex configurations involving UI Builder, Mobile App
    Builder, Flow Designer, or other builder tools
-   Create ATF tests / suites for applications
-   Collaborate with system administrator to create Instance Scan
    definitions for the platform

**Role(s) required**
-   delegated_developer
-   sn_app_eng_studio.user
-   atf_test_admin
-   scan_admin

Low-Code / Citizen Developer
{: .fs-6 }

**Responsibilities**

-   Submit requests for new custom applications to build in App Engine
    Studio
-   Understand ServiceNow and application development best practices
-   Build and test applications in App Engine Studio
-   Submit developed App Engine Studio applications for IT review
-   Maintain and modify the application during its lifecycle if

**Role required**
- sn_app_eng_studio.user

[Back to top](#top){: .btn .btn-purple }

---

# Prepare environments for App Engine Studio {#prepare-environments-for-app-engine-studio}

Before installing App Engine Studio, review all platform requirements and define an organizational instance strategy to prepare for successful installation and configuration.

## Review platform requirements
- App Engine Studio Version 22.0.3
- App Engine license required
  -	Contact your ServiceNow Account Manager for additional information on App Engine, or see [ServiceNow App Engine](https://www.servicenow.com/products/now-platform-app-engine.html)
- Instances must be on Tokyo release
- **admin** role is required in all instances to install App Engine Studio and dependent applications from the ServiceNow Store

## Define instance strategy
When defining the instance strategy for App Engine Studio, it is recommended to leverage one production instance and at least two sub-production instances – however App Engine Studio can support any number of sub-production instances as part of an instance strategy.

Applications are deployed to the production instance once developed and successfully tested in sub-production instances. One sub-production instance will serve as the development environment, and the other as the test environment.

If your organization uses sandbox or staging environments in addition to test and development, they can be incorporated to the instance strategy accordingly based on organizational needs.

![](/images/image3.png)


*Example instance strategy with one production instance and three sub-production instances*

Sub-production instances that are most similarly configured to your production instance are the best candidates for test and stage environments. This way, administrators can more accurately find issues that may arise if the application is deployed to production.

*For more information, see [[Product Documentation: Instance strategy for App Engine Studio]](https://docs.servicenow.com/csh?topicname=aes-instance-strategy.html)*

[Back to top](#top){: .btn .btn-purple }

---

# How do I install App Engine Studio? {#how-do-i-install-app-engine-studio}

## Opt-in and manage entitlements {#opt-in-and-manage-entitlements}

Before installing the application from the ServiceNow Store, verify the instance has valid ServiceNow entitlements.

In the ServiceNow Store, use the search criteria to find App Engine Studio.

![](/images/image4.png)
 
Click **Opt-in** and agree to the ServiceNow terms and conditions to verify entitlements.

Click **Manage Entitlements** and set the 'Entitlement Type' value to **Entitle all Instances** (*if you prefer to manually select which instances which will be affected, select Entitle Selected Instances).*

## Install App Engine Studio application {#install-app-engine-studio-application}

To install the App Engine Studio application (***com.snc.app-engine-studio***), login to your [development] instance and navigate to the ServiceNow Store.

Use the search criteria to find the App Engine Studio application. Click **Install / Update All**.

![](/images/image5.jpeg)
 
The App Engine Studio bundle will be installed in the development instance-- including the App Engine Studio application and all dependent applications.

Repeat this process on all instances for cloning purposes.

*For more information, see:*

-   [*[ServiceNow Store: Install a ServiceNow Product]*](https://store.servicenow.com/%24appstore.do%23!/store/help?article=KB0030186)

-   [*[Product Documentation: Install App Engine Studio]*](https://docs.servicenow.com/csh?topicname=install-aes.html)

[Back to top](#top){: .btn .btn-purple }

---

# How do I configure App Engine Studio? {#how-do-i-configure-app-engine-studio}

![](/images/image6.jpeg)

***\*\*** Repeat steps across all sub-production instances, as necessary*

***Note:** If you plan on cloning your production instance to one or more sub-production instances, install all App Engine Studio plugins on all instances prior to cloning, and enable ATF and Instance Scan properties in your production instance. Additionally, the AEMC plugin must be installed on all instances to appropriately collect application and developer data on development. For more information, see [[Product Documentation: System clone]](https://docs.servicenow.com/csh?topicname=c_SystemClone.html)*

The App Engine Studio bundle has three Guided Setup modules to assist in configuration:

[**App Engine Studio Guided Setup**](#app-engine-studio-guided-setup)

  -   Configure foundational application components and provision initial
    user access

[**Pipeline and Deployment Guided Setup**](#pipeline-and-deployment-guided-setup)

  -   Configure pipelines to deploy applications across instances with
    confidence

[**Application Intake Guided Setup**](#application-intake-guided-setup)

  -   Configure application intake catalog item and process to enable
    business users to submit application requests from an existing
    service portal

***Note:** App Engine Management Center is dependent on the configuration of Pipelines and Deployment Guided Setup, and optionally Application Intake Guided Setup*

*For more information, see [Product Documentation: Using guided setup](https://docs.servicenow.com/csh?topicname=guided-setup.html)*

## App Engine Studio Guided Setup
*Part of: How do I configure App Engine Studio?*

Navigate to **App Engine Studio \Configuration \Guided Setup** in your development instance to access the App Engine Studio Guided Setup.

![](/images/image7.png)

***Note**: Before beginning App Engine Studio Guided Setup, ensure your application scope is set to 'App Engine Studio'. If not, use the application picker to change the current session's scope*

![](/images/image8.jpeg)


**Review and set up tooling in the development instance**

Review and update App Engine Studio developer access to builder tools during development.

**Connect spokes in development**

A spoke is a scoped application that contains Flow Designer or Integration Hub actions or sub-flows.

System Administrators can connect IntegrationHub spokes to App Engine Studio, allowing developers to integrate custom applications with third-party systems. For example -- connecting the Slack spoke allows developers to post a message containing Incident details to a specific Slack channel each time a high priority Incident is created.

Many Integration Hub spokes are available, but not all need to be connected to App Engine Studio. Review some of the common spokes below and install based on organizational needs.

```
+----------------------+-----------------------------------------------+
| **Integration Hub    | **Installing this spoke provides              |
| spoke**              | developers...**                               |
+======================+===============================================+
| Microsoft Teams      | Actions to support cross-functional           |
|                      | communications and collaborations in          |
|                      | Microsoft Teams.                              |
+----------------------+-----------------------------------------------+
| Slack                | Actions to automate the management of Slack   |
|                      | channels, users, and software subscriptions.  |
+----------------------+-----------------------------------------------+
| Jira                 | Actions to automate tasks in Jira for         |
|                      | managing users, issues, projects, and         |
|                      | software development lifecycle.               |
|                      |                                               |
|                      | Synchronize data in ServiceNow with Jira to   |
|                      | increase collaboration between ServiceNow     |
|                      | users and DevOps teams.                       |
+----------------------+-----------------------------------------------+

  -----------------------------------------------------------------------
  Gmail                   Actions to automate email and label management
                          in Google Gmail.
  ----------------------- -----------------------------------------------
  Microsoft Azure AD      Actions to automate Microsoft Azure Active
                          Directory tasks for user management,
                          authentication, and group membership.

  Twitter                 Actions to automate posting messages and media
                          content to a corporate Twitter news feed.

  Microsoft 365 Excel     Actions to automate worksheet, table, and cell
                          management in Microsoft Excel.
  -----------------------------------------------------------------------

```

This step is not required as part of the initial application setup.

As your organization's citizen development program matures and scales, additional spokes can be installed and connected based on application demand and use cases.

*For more information on integrations with third-party systems, see [Product Documentation: Integration Hub](https://docs.servicenow.com/csh?topicname=integrationhub.html)*

**Review Flow Designer access settings from App Engine Studio in development**

Review and update App Engine Studio developer access settings to Flow Designer Resources and update as necessary.

Developers can leverage Flow Designer capabilities while creating logic and automation for custom applications.

Consider restricting developer access to Flow Designer Resources using content filtering for Flow Designer. This allows administrators to manage access to Flow Designer resources and specify which features App Engine Studio users can leverage while building applications.

![](/images/image9.jpeg)

This step is not required as part of the initial application setup.

Flow Designer access from App Engine Studio can be updated later to provide developers the editing capabilities that best suit their experience and needs.

*For more information on Flow Designer resources, see [[Product Documentation: Content Filtering for Flow Designer]](https://docs.servicenow.com/csh?topicname=content-filtering-flow-designer.html)*

**Review Service Catalog access settings in development**

Review App Engine Studio developer access to the Catalog Builder tool's catalog item templates and catalogs / categories, and update access as necessary.

By default, App Engine Studio developers can leverage catalog templates to quickly create record producers or catalog items. Developers can also publish catalog items to any catalog. If you wish to limit access to templates or restrict publishing access to catalogs or categories, update the access accordingly in Catalog Builder.

![](/images/image10.png)


This step is not required as part of the initial application setup.

Catalog access from App Engine Studio can be updated at a later point to modify developer access to App Engine Studio catalogs, categories, and catalog templates.

*For more information on creating or editing catalog items, see
[[Product Documentation: Catalog Builder]](https://docs.servicenow.com/csh?topicname=catalog-builder.html)*

**Configure Instance Scan definitions**

Deploy custom applications with confidence by setting up Instance Scan definitions to monitor instance health throughout the deployment process. Instance scans interrogate your instance for configurations and health issues, allowing administrators an opportunity to address best practices and to avoid similar configuration issues in the future.

Instance Scan definitions are executed automatically when App Engine Studio applications are promoted to the **Testing** instance. Instance Scan results will be logged in the Notes section of the Deployment Request record.

The App Engine Studio application does not ship with any out-of-box Instance Scan definitions (however a few Instance Scan definitions are installed with the Deployment Pipeline plugin to run basic performance checks).

Work with professional ServiceNow developers to configure Instance Scan definitions and enforce best practices in your environments.

![](/images/image11.jpeg)

**Enable and configure Instance Scan properties in your production instance if you plan to clone!**

*For more information on managing instance health scans, see [[Product Documentation: Instance Scan]](https://docs.servicenow.com/csh?topicname=hs-landing-page.html)*

**Set up user access**

Configure the admin group and other general settings for App Engine Studio users.

**Set up administrator group in development**

Configure App Engine Studio administrator group membership in the [development] instance to manage development activities that occur in the development environment.

![](/images/image12.jpeg)


While development activities will be managed in the [development] instance, administrators manage application intake, collaboration, and deployment requests in [production].

Group membership does not sync across instances; therefore, system administrators are required to add users in both the development and production instances.

***Note**: Group membership does not sync across instances, therefore App Engine Studio administrator group membership will also need to be provisioned in the [production] instance as part of the Pipelines and Deployment or Application Intake Guided Setup activities*

b.  **Grant access to current developers in development**

Allow existing application developers who are already assigned the **delegated_developer** role access to the App Engine Studio application by adding them to the 'App Engine Studio Users' assignment group.

***Note:** If you wish to grant multiple developers access at one time, advance to the next step to manage access more efficiently*

c.  **Grant access to other users in development**

After provisioning access for existing developers, grant App Engine Studio access to other users within the organization by adding them to the 'App Engine Studio Users' group.

![](/images/image13.png)

[Back to top](#top){: .btn .btn-purple }

---

## Pipeline and Deployment Guided Setup
*Part of: How do I configure App Engine Studio?*

Once App Engine Studio Guided Setup has been completed, administrators must complete the Pipeline and Deployment Guided Setup activities.

Pipelines enable you to automate the propagation and installation of your applications from one instance to another. Pipelines are powered by the ServiceNow CI / CD spoke, which enables you to automate processes such as publishing applications to the application repository, installing them on target instances, and running ATF tests and/or instance scans.

To access the Pipeline and Deployment Guided Setup, navigate to **App Engine Studio \Pipelines and Deployment \Guided Setup**.

Pipeline and Deployment Guided Setup activities do not sync across instances and Pipeline configuration activities are required on all instances (production and sub-production).

Refer to the process flow on page **[9]** for an overview of the Pipeline and Deployment Guided Setup.

![](/images/image14.jpeg)

***Note**: Before beginning Pipelines and Deployment Studio Guided Setup, ensure your application*

*scope is set to '**Deployment Pipeline**'. If not, use the application picker to change the current session's scope*

![](/images/image15.png)

1.  **[Configure your production instance]**

In the [production] instance, complete the following steps to configure environments and deployment pipelines to streamline your application deployment process**.**

**Complete these tasks only if you are logged into your production instance.**

a.  **Install 'Deployment Pipeline' plugin in production instance**

To install the Deployment Pipeline plugin, (***com.snc.deployment-pipeline**)*, login to your production instance and navigate to **System Definition \Plugins.**

Use the search criteria to find the application. Click **Install**.

![](/images/image16.png)

***Note:** If you have already installed the App Engine Studio bundle in the development instance and promoted up to production, skip this step*

b.  **Configure credentials in production instance**

Credentials allow your production instance to communicate with sub-production instances.

In production, navigate to Connections & Credentials \Connection & Credential Aliases.

Only users assigned the admin role can create and update Credential Alias records.

![](/images/image17.png)

Credential Alias

```
+----------------+-----------------------------------------------------+
| Field          | Description                                         |
+================+=====================================================+
| Name           | Name of the Credential Alias. This alias associates |
|                | to Credential data only and resolves the            |
|                | application integration for each environment.       |
|                |                                                     |
|                | An alias can only contain alpha, number, or         |
|                | underscore characters. This should be an easily     |
|                | identifiable name, as it will be referenced when    |
|                | creating Environment records in later steps         |
|                | (Pipeline Credentials,                              |
+----------------+-----------------------------------------------------+
| Type           | Ensure the 'Type' value is set to Credential when   |
|                | creating                                            |
|                |                                                     |
|                | Credential Alias records for App Engine Studio.     |
+----------------+-----------------------------------------------------+

+----------------+-----------------------------------------------------+
|                | The default value is Connection and Credential and  |
|                | will need to be updated.                            |
+================+=====================================================+
| Application    | The application scope against which the Credential  |
|                | Alias is assigned.                                  |
|                |                                                     |
|                | Ensure the value in the 'Application' field shows   |
|                | as App Engine Studio. If the 'Application' field is |
|                | not populating as expected, use the application     |
|                | picker to change the current session's scope.       |
+----------------+-----------------------------------------------------+
| ID             | The unique identifier for the Credential Alias      |
|                | record.                                             |
|                |                                                     |
|                | This value auto-populates after record creation     |
|                | based on the format scope_name.alias_name and is    |
|                | read-only.                                          |
+----------------+-----------------------------------------------------+
```

Based on the credential information, take the appropriate approach in configuring Credential Alias records:

-   If all environments in the Deployment Pipeline will use the [same] credential information (same username/password), then only [one] Credential Alias record will be configured in production
    -   i.e., single Credential Alias record named '*Pipeline
        Credentials'*

-   However, if each environment in the Deployment Pipeline will use different credentials (different usernames / passwords), then Credential Alias records will be created for each instance in the production instance

    -   i.e., multiple Credential Alias records named 'Dev Credentials', 'Test Credentials', 'Stage Credentials', and 'Prod Credentials'

Once the necessary Credential Alias record(s) have been created, navigate to the 'Credentials' Related List and click New to add credential
details.

Select Basic Auth Credentials to populate the Basic Auth Credential form (currently, this is the only Credential type supported by App Engine Studio).

![](/images/image18.jpeg)

It is recommended to use a username / password for a service account so that the password does not expire or change. The account [must exist in the] [target instance(s) and have admin permissions.]

*For more information, see [[Product Documentation: Create a Connection & Credential Alias]](https://docs.servicenow.com/csh?topicname=connection-alias.html)*

c.  **Configure environments in production instance**

Set up and configure the environments that will be included within your pipelines. These will be referenced when building your pipelines.

Your production instance is where your pipeline configurations reside and will be your controller instance.

**The 'Is Controller?' box will be [checked] on your production instance only. This box will be [unchecked] for all sub-production Environment records.**

![](/images/image19.jpeg)

**Environments**

```
+----------------+-----------------------------------------------------+
| **Field**      | **Description**                                     |
+================+=====================================================+
| Name           | Name of the environment.                            |
+----------------+-----------------------------------------------------+
| Instance Type  | Purpose the instance serves in the Deployment       |
|                | Pipeline (i.e., sandbox, development, testing,      |
|                | staging, production).                               |
+----------------+-----------------------------------------------------+
| Instance URL   | URL for the instance. Must begin with **http://**   |
|                | or **https://**                                     |
+----------------+-----------------------------------------------------+
| Instance ID    | Auto-generated ID value based on Instance URL       |
+----------------+-----------------------------------------------------+
| Application    | Application scope against which the Environment is  |
|                | assigned.                                           |
|                |                                                     |
|                | Ensure the value in the 'Application' field shows   |
|                | as **App Engine Studio**. If the 'Application'      |
|                | field is not populating as expected, use the        |
|                | application picker to change the current session's  |
|                | scope.                                              |
+----------------+-----------------------------------------------------+
| Instance       | ID of the Credential Alias record (displays as      |
| credential     | **scope_name.alias_name**). This should point to    |
|                | the Credential Alias record for the environment     |
|                | being set up.                                       |
|                |                                                     |
|                | For example, creating an Environment record for a   |
|                | development instance:                               |
+----------------+-----------------------------------------------------+

+----------------+-----------------------------------------------------+
|                | -   **Name**: My Company's Dev Instance             |
|                |                                                     |
|                | -   **Instance Type: '**Development'                |
|                |                                                     |
|                | -   **Instance URL:**                               |
|                |     [[https://mycompanydev.service-now.com]{        |
|                | .underline}](https://mycompanydev.service-now.com/) |
|                |                                                     |
|                | -   **Instance Credential:** Dev AES Pipeline       |
|                |     Credential                                      |
|                |                                                     |
|                | -   **Is Controller**?: Unchecked                   |
+================+=====================================================+
| Is Controller? | Indicates the Controller instance of a pipeline.    |
|                |                                                     |
|                | The Controller is the instance where pipeline       |
|                | configurations are captured, sub-flows run, and     |
|                | where all App Engine Studio requests are created.   |
|                |                                                     |
|                | This field should only be checked for an instance   |
|                | of type                                             |
|                |                                                     |
|                | **Production**!                                     |
+----------------+-----------------------------------------------------+
```

*For more information, see [[Product Documentation: Define environments]](https://docs.servicenow.com/csh?topicname=create-environment.html)*

a.  **Configure pipelines in production instance**

A pipeline defines the path an application takes from the development to production environments and allows administrators to quickly move applications across instances.

Set up and configure your pipelines by specifying the environments to include along with their position in the pipeline.

![](/images/image20.png)


**Pipelines**

```
  -----------------------------------------------------------------------
  **Field**         **Description**
  ----------------- -----------------------------------------------------
  Name              Name of the pipeline.

  Pipeline Type     Purpose of the development pipeline.

  Source            The environment where development activities take
  Environment       place in the deployment pipeline.
  -----------------------------------------------------------------------
```

```
+----------------+-----------------------------------------------------+
|                | Each pipeline must have a unique Source             |
|                | environment.                                        |
+================+=====================================================+
| Application    | Application scope against which the Pipeline record |
|                | is assigned.                                        |
|                |                                                     |
|                | Ensure the value in the 'Application' field shows   |
|                | as **App Engine Studio**. If the 'Application'      |
|                | field is not populating as expected, use the        |
|                | application picker to change the current session's  |
|                | scope.                                              |
+----------------+-----------------------------------------------------+
| Active         | Option to activate the pipeline.                    |
|                |                                                     |
|                | The 'Submit' button will not be available for App   |
|                | Engine Studio developers unless there is an active  |
|                | pipeline where the source environment is the        |
|                | instance where the App Engine Studio application is |
|                | installed.                                          |
+----------------+-----------------------------------------------------+
```

Once a pipeline has been created, use the **Pipeline Environments Order** Related List on the Pipeline record to configure the instance order for the pipeline. Create a record in the related list for all instances *[except]* the development instance and specify the environment's order within the pipeline.

Application movement across pipelines is dictated by the order of the environments in the Pipeline Environment Order related list, and applications are promoted based on ascending 'Order' values.

Be sure the environment order is consistent with the defined instance strategy. The production instance should have the highest 'Order' value *(i.e., Testing: 100, Staging: 200, Production: 300).*

![](/images/image21.jpeg)

***Note:** Since the development environment is already identified as the 'Source Environment' on the Pipeline record, a Pipeline Environment Order related record is not required*

**Pipeline Environment Orders**
```
+----------------+-----------------------------------------------------+
| **Field**      | **Description**                                     |
+================+=====================================================+
| Pipeline       | Refers to the pipeline type.                        |
+----------------+-----------------------------------------------------+
| Environment    | The environment being added as part of the          |
|                | deployment pipeline.                                |
+----------------+-----------------------------------------------------+
| Order          | Order in which the environment exists in the        |
|                | pipeline.                                           |
|                |                                                     |
|                | Applications move through the pipeline in is        |
|                | ascending order.                                    |
+----------------+-----------------------------------------------------+
| Application    | Application scope against which the Pipeline        |
|                | Environment Order record is assigned.               |
|                |                                                     |
|                | Ensure the value in the 'Application' field shows   |
|                | as **App Engine Studio**. If the 'Application'      |
|                | field is not populating as expected, use the        |
|                | application picker to change the current session's  |
|                | scope.                                              |
+----------------+-----------------------------------------------------+
```

*For more information, see [[Product Documentation: Create a pipeline]](https://docs.servicenow.com/csh?topicname=create-pipeline.html)*

b.  **Add users to the App Engine Studio Administrators group in production instance**

Configure App Engine Studio administrator group membership in the [production] instance to manage application intake and deployment requests.

Ensure the group membership in [production] is consistent with the App Engine Studio administrators identified in the [development] instance.

Group membership does not sync between environments and must be updated in both production and development.

***Note:** If group membership is empty in the production instance, or if the Deployment Pipeline plugin is not installed, the system will refer to App Engine Studio Administrator group membership in the development instance*

2.  **[Configure sub-production instances]**

Follow the steps below to install the 'Deployment Pipeline' plugin in each [sub-] [production] instance.

Once installed, you will be required to configure an environment record in each instance which points to the production (controller) instance.

You will also enable the system properties that will allow the Automated Test Framework (ATF) suite to run during the deployment process.

**Complete these tasks only if you are logged into a sub-production instance.**

a.  **Install the 'Deployment Pipeline' plugin in each sub-production instance**

To install the Deployment Pipeline plugin, (*com.snc.deployment-pipeline)*, login to any sub-production instance and navigate to **System Definition \Plugins.**

Use the search criteria to find the application. Click **Install**.

Repeat and install the Deployment Pipeline plugin in each sub-production instance.

![](/images/image22.png)

***Note:** If you have already installed the App Engine Studio bundle in the development instance and promoted up to production, skip this step*

**Repeat this task on each sub-production instance that will be part of a pipeline**

b.  **Configure credentials in each sub-production instance**

In each sub-production instance, create a Credential Alias record and associate the Credentials for the production instance.

Navigate to Connections & Credentials \Connection & Credential Aliases.

Based on the credential information, take the appropriate approach in configuring Credential Alias records:

![](/images/image17.png)


-   If all environments in the Deployment Pipeline will use the [same] credential information (same username / password), then create a single Credential Alias record with the same details as the Credential Alias created in the production instance

-   i.e., single Credential Alias record named '*Pipeline Credentials'*

-   If each environment in the Deployment Pipeline will use [different] credentials (different usernames / passwords), then create a single Credential Alias records with the credential details for the production instance

    -   i.e., single Credential Alias records named '*Prod Credentials'*

**Repeat this task on each sub-production instance that will be part of a pipeline,**

***Note**: Ensure the username(s) and password(s) provided exist in the production instance and the User is assigned the correct roles.*

c.  **Configure the controller instance in each sub-production instance**

In each sub-production instance, set up and configure the Environment record which will point to the controller instance ([production] instance), where the Deployment Pipeline configurations reside.

All deployment requests are routed through the controller instance. Until this is configured, your developers will not be able to submit deployment requests.

If a Credential Alias record for the controller (production) instance has not been created in each sub-production instance, you must create a Credential Alias record pointing to the controller instance in each sub-production instance.

If App Engine Studio is the only application using the Credentials table, consider creating data preservers for Credential Alias, Basic Auth, and Discovery credentials -- otherwise, ensure that these tables are not overwritten when the production instance is cloned down to sub-production instances.

App Engine Studio has data preservers on the following tables:
-   Pipeline Instance
-   Request Authorization Key
-   Deployment Request
-   Deployment Environment Request

To ensure application and developer data is not lost in development environments during a clone, add **data preservers** to the following:

-   Collaboration Descriptor tables:
-   App Collaboration Descriptors **\[sys_appcollab_descriptor\]**
-   App Collaboration Descriptor Permissions **\[sys_appcollab_permission_m2m\]**
-   Collaboration Users and Groups tables:
-   App Collaboration Users **\[sys_appcollab_user\]**
-   App Collaboration Groups **\[sys_appcollab_group\]**

Additionally, add **clone excludes** for the following Collaboration Descriptor tables. so that data in these tables are preserved after cloning and that no data from the source instance gets copied over. It is ok to have data merge from source and target for collaboration users and groups tables.

-   App Collaboration Descriptors **\[sys_appcollab_descriptor\]**
-   App Collaboration Descriptor Permissions **\[sys_appcollab_permission_m2m\]**

After cloning, a post-clone clean-up script is needed to reassign users and groups the appropriate delegated development permissions. We assume that in-development applications are backed up before cloning and users/groups are same between target and source instance.

**Repeat this task on each sub-production instance that will be part of a pipeline**

***Note:** New App Engine Studio customers (Tokyo +) will only have data preservers on the tables listed above. Existing customers (pre-Tokyo) will also have data preservers on the following tables : Pipeline, Environment. Pipeline Environment Order, Pipeline Types*

a.  **Enable Automated Test Framework (ATF) properties (*testing instance only*)**

Enable the system properties that will allow the ATF suite to run in the testing instance as part of the deployment process.

App Engine Studio ships with an out-of-box test suite as a placeholder, however you are responsible for configuration of the ATF tests. If the out-of- box suite is not modified, they will still run but will not impact the flow.

![](/images/image23.jpeg)

-   **Enable test / test suite execution *(sn_atf.runner.enabled)***
    -   Check this box on the ***[testing]*** instance to enable automated tests to run as part of the application deployment process
    -   The default value is false so that ATF tests do not run on production instances
    -   This property is private; changes to its value will not move between instances
        -   **Enable scheduled test suite execution *(sn_atf.schedule.enabled)***
    -   The 'Enable test / test suite execution' property must be enabled to enable this property

-   Check this box on the ***[testing]*** instance to enable scheduled automated test suites to run as part of the application deployment process

-   The default value is false so that ATF tests do not run on production instances

-   This property is private; changes to its value will not move between instances

If you do not enable these properties on the testing instance you will receive a warning during the deployment process, but you will be able to continue with deployment and the flow will continue.

**Enable ATF properties in your production instance if you plan to clone!**

***Note**: Ensure that the controller instance was configured on all sub-production instances that are part of a pipeline!*

[Back to top](#top){: .btn .btn-purple }

---

## Application Intake Guided Setup
*Part of: How do I configure App Engine Studio?*

Navigate to **App Engine Studio \Application Intake \Guided Setup** in your [production] instance to access the Application Intake Guided Setup.

![](/images/image24.jpeg)

***Note**: Before beginning Application Intake Guided Setup, ensure your application scope is set to 'Application Intake'. If not, use the application picker to change the current session's scope.*

![](/images/image25.png)


1.  **[Turn on and configure the intake request process in production]**

You'll need to activate the catalog item on your **production instance** and configure settings to enable auto-provisioning of users to a development instance if their intake request is approved.

a.  **Activate the catalog item where developers will submit their application ideas**

![](/images/image26.jpeg)


Activate the 'Apply for Citizen Development' catalog item and allow developers to submit application ideas for screening by the App Engine Studio Administrators.

The application intake request is used to capture information from business users submitting application ideas to the App Engine Studio Administrators group for review.

Administrators can modify the out-of-box catalog item in Catalog Builder according to organizational needs so that all necessary information is captured from requestors.

b.  **Activate user provisioning**

![](/images/image27.jpeg)

Activate the property on your [production] instance to allow the system to provision users to the App Engine Studio Users group in a target development instance upon the approval of an application intake request.

Set the value of the **sn_app_intake.instance_can_provision_users** system property to **true**.

2.  **[Configure development environments for users]**

You'll need to activate the catalog item on your **production instance** and configure settings to enable auto-provisioning of users to a development instance if their intake request is approved.

a.  **Create environment record(s) for development instances in production**

In the [production] instance, create new Environment records for each development environment you would like to provision users to upon approving application intake requests. For the user provisioning to work on the target instances, the 'Instance Type' value must be set to **Development**.

If these records have already been setup as part of the Pipelines and Deployment Guided Setup, skip this step

***Note:** For the Application Intake plugin to work correctly, App Engine Studio must be installed on the production instance*

[Back to top](#top){: .btn .btn-purple }

---

# How do I manage App Engine Studio access? {#how-do-i-manage-app-engine-studio-access}

## Grant and revoke access {#grant-and-revoke-access}

When user provisioning has been configured as part of the Application Intake Guided Setup, users are automatically added to the App Engine Studio Users assignment group (in the target development instance) upon the approval of a submitted application intake request.

Additionally, system administrators can manually manage group membership to the 'App Engine Studio Users assignment group by navigating to **All \User Administration \Groups** and opening the 'App Engine Studio Users' record.

Once added to the group, members are assigned the **sn_app_eng_studio.user** role, allowing them to access and build in App Engine Studio.

[Before granting access to the App Engine Studio application, ensure users have completed the] [appropriate citizen development learning paths and trainings available in Now Learning!]

![](/images/image28.png)

**Considerations for development security:**

-   Ensure an application owner and support team(s) have been identified to own and support the application once in production
-   Add users to the 'App Engine Studio Users' assignment group instead of assigning the **sn_app_eng_studio.user** role to users directly
-   Consider creating multiple App Engine Studio developer groups to accommodate developers of different skill / experience levels
    -   i.e., one assignment group for experienced developers with enhanced permissions, and another group for less experienced developers with restricted access to platform features -- managed via delegated development

*For more information, see [[Product Documentation: Grant access to App Engine Studio]](https://docs.servicenow.com/csh?topicname=grant-aes-access.html)*

[Back to top](#top){: .btn .btn-purple }

---

## Manage collaboration and delegated development {#manage-collaboration-and-delegated-development}

In App Engine Studio, application owners can submit collaboration requests to have other users added as collaborators to assist them in delivering applications.

App Engine Studio's collaboration feature uses delegated development, allowing application owners to pick the level of access collaborators have to an application.

The **admin** role is required to create custom App Engine Studio roles available to developers when adding collaborators.

![](/images/image29.jpeg)


When a collaboration request is submitted and the collaborator already has access to App Engine Studio (belongs to the 'App Engine Studio Users' group), then the request will be approved automatically.

If the requested collaborator does not already have access, App Engine Studio administrators are responsible for reviewing assigned Collaboration Task details. When approved, the system will automatically grant App Engine Studio access for the requested collaborator in the specified target development instance

App Engine Studio administrators can access Collaboration Requests in the [production] instance from the App Engine Management Center or by navigating to **App Engine \Collaboration \> Collaboration Tasks.**

For more information, see: *[[Product Documentation: Delegated development in App Engine]](https://docs.servicenow.com/csh?topicname=aes-app-dev-workflow.html) [[Studio]](https://docs.servicenow.com/csh?topicname=aes-app-dev-workflow.html)*

[Back to top](#top){: .btn .btn-purple }

---

# How do I manage application intake requests? {#how-do-i-manage-application-intake-requests}

***Note**: Before editing the Application Intake process, ensure your application scope is set to **'**Application Intake'**. If not, use the application picker to change the current session's scope*

![](/images/image30.png)

[Back to top](#top){: .btn .btn-purple }

---

## Configure the application intake request form {#configure-the-application-intake-request-form}

Administrators can configure the out-of-box application intake request form to capture the necessary information from custom application requestors, according to organizational needs. The intake form is installed with the **Application Intake** plugin and can be modified in Catalog Builder.

## Access and review application intake requests {#access-and-review-application-intake-requests}

When application ideas are submitted by requestors, approval records are created and assigned to users in the App Engine Studio Administrators group.

App Engine Studio administrators can access assigned requests in the [production] instance from the App Engine Management Center or by navigating to **Self Service \Requested Items**.

App Engine Studio Administrators will receive an email notification when intake requests are submitted. Administrators are responsible for reviewing the submitted application requests to determine if they are a suitable use case for development in App Engine Studio.

## Choosing the right applications for App Engine Studio {#choosing-the-right-applications-for-app-engine-studio}

The first step in evaluating application requests is to make sure the request is not already satisfied by an existing application or will not be addressed as part of an upcoming ServiceNow release.

Administrators are then responsible for determining if App Engine Studio is the appropriate development environment for the application.

Ideal use cases for App Engine Studio development include:

-   Use cases where an application template already exists in App Engine Studio
-   Simple processes that are easily translated to automated workflows
-   Departmental processes managed by subject matter experts
-   Applications with simple third-party integrations
-   No confidential or sensitive data involved

Even if an application requires advanced development, the foundational application work can be completed in App Engine Studio, and pro-code developers can easily transfer applications to ServiceNow Studio to perform complex development activities.

If the proposed application is a good candidate for development in App Engine Studio, click **Approve.** The requestor will receive an email notification informing of the request approval. App Engine Studio administrators are responsible for manually provisioning App Engine Studio access for requestors so they can begin building their applications.

Before approving an application, be sure the application requestor has identified the application owner and support team(s) responsible for owning and managing the application once it is in production.

If the request is not viable, click **Reject.** The requestor will receive an email notification informing of the rejection.

***Note**: Consider creating an assessment and risk profile to assist in screening application requests. An assessment can be configured to capture the application details. Based on the development effort required, application inputs / outputs, or other factors, a risk score will be generated for the application request.*

*Using the risk score, define a threshold for applications that are good candidates for App Engine Studio, or if they should instead be developed in ServiceNow Studio (i.e., if risk score is Low or Medium, the application will be approved for App Engine Studio development -- if the risk score is High, consider building the application in ServiceNow Studio).*

*For more information, see [[Product Documentation: Intake request process for application]](https://docs.servicenow.com/csh?topicname=intake-request.html&intake-request) [[development ideas]](https://docs.servicenow.com/csh?topicname=intake-request.html&intake-request)*

[Back to top](#top){: .btn .btn-purple }

---

# How do I manage application deployment requests? {#how-do-i-manage-application-deployment-requests}

Deployment Requests are used to track and manage an application's movement across instances.

App Engine Studio Administrators can access deployment requests in the production instance from the App Engine Management Center or by navigating to **App Engine Studio \Configuration \App Deployment Request**.

When an application is submitted for IT review, the system generates and assigns a Deployment Request record to the App Engine Studio Administrators group.

Administrators can review application, requestor, and deployment details from the Deployment Request. Pipeline and environment information for applications are available in the 'Deployment Details' section of the request form.

![](/images/image31.png)


**Deployment Request States**

```
+----------------+-----------------------------------------------------+
| **State**      | **Description**                                     |
+================+=====================================================+
| New            | An application has been submitted for IT review by  |
|                | an App Engine Studio developer.                     |
|                |                                                     |
|                | The State will automatically change from **New** to |
|                | **In Review** once the first sub-flow in the        |
|                | Deployment Pipeline has finished executing.         |
+----------------+-----------------------------------------------------+
| In Review      | Application is under review by the App Engine       |
|                | Studio administrators.                              |
|                |                                                     |
|                | Review and testing activities occur in the Testing  |
|                | instance.                                           |
+----------------+-----------------------------------------------------+
| Closed --      | Application has been successfully published to the  |
| Published      | production instance.                                |
+----------------+-----------------------------------------------------+
| Closed --      | Application has failed testing and is not ready to  |
| Rejected       | be published to the production instance.            |
+----------------+-----------------------------------------------------+
| Closed --      | Indicates a sub-flow in the Deployment Pipeline     |
| Failed         | failed.                                             |
+----------------+-----------------------------------------------------+
| Cancelled      | The Deployment Request was cancelled.               |
+----------------+-----------------------------------------------------+
```

## Promote an application in a pipeline {#promote-an-application-in-a-pipeline}

When application developers submit an application for IT review, App Engine Studio administrators are assigned Approval records for the Deployment Requests.

Applications are promoted to the next instance in the Deployment Pipeline when administrators approve a request. Only one administrator is required to approve or reject a request.

If a request is approved, the system will trigger a sub-flow to promote the application to the next environment, as defined by Deployment Pipeline configuration.

Each time an application is promoted to a new instance administrators will be assigned a new Approval record. When approved, the application will be promoted to the next instance in the pipeline. This continues until the application is promoted to the production instance.

## Review and test an application {#review-and-test-an-application}

Once an application has been promoted to the Testing instance, it should be thoroughly tested and reviewed by the application developer, experienced ServiceNow developers, and functional IT resources to ensure that the application works as expected and existing platform functionality is not impacted. Assign application roles in the test environment appropriately so that users can complete necessary testing activities.

As part of the application deployment process, Automated Test Framework (ATF) tests / suites and Instance Scan definitions will automatically run when the application is promoted to an instance of Type = Testing (if multiple instances are configured with Type = Testing, then the test suites and definitions will run on each instance). ATF and Instance Scan results will be logged in the Notes section of the Deployment Request and available in the 'Deployment
Environment Results' related list.

As your citizen development program scales, consider implementing an application 'risk profile' to dictate the level of testing required to more efficiently allocate testing resources. For example, an application containing a Script Include will have a higher risk profile than an application built with a template and minimal configurations, and therefore will require more rigorous testing).

## Reject an application {#reject-an-application}

If an application fails testing or requires additional development work, administrators can reject an application by clicking **'Reject'** on the assigned approval record.*

If you reject an application, provide clear feedback to developer(s) so they can quickly correct the configurations. The Deployment Request 'State' will change to **Closed -- Rejected** and the requestor will receive an email notification informing of the rejection.

Application developers can incorporate feedback and continue to submit the application for IT review.

*For more information, see:*

-   [*[Product Documentation: Deployment Request form]*](https://docs.servicenow.com/csh?topicname=deployment-request-form.html)

-   [*[Product Documentation: Move an application to your test environment]*](https://docs.servicenow.com/csh?topicname=move-app-instance.html)

-   [*[Product Documentation: Reject an application]*](https://docs.servicenow.com/csh?topicname=approve-reject-app.html)

# How do I deploy applications to production in App Engine Studio? {#how-do-i-deploy-applications-to-production-in-app-engine-studio}

Once an application has successfully completed all testing activities from required reviewers, it is ready to be promoted to the production instance.

When administrators approve an application to promote an application to production, the Deployment Request 'State' will change to **Closed -- Published**. The application will be published to the application repository and installed on the production instance. Assign roles appropriately so that users can access the application across instances, as necessary.

![](/images/image32.png)
 
For more information, see:

- [[*Product Documentation: Deploy an application*]](https://docs.servicenow.com/csh?topicname=deploy-app.html)
- [[*Product Documentation: Application sharing*]](https://docs.servicenow.com/csh?topicname=c_SharingApplications.html)
- [[*Product Documentation: Publish an application to the application repository]*](https://docs.servicenow.com/csh?topicname=t_PublishAppsToTheAppRepository.html)

[Back to top](#top){: .btn .btn-purple }

---

# How do I create application templates? {#how-do-i-create-application-templates}

App Engine Studio offers developers pre-configured application templates that can be used to jumpstart development and accelerate time to value. In addition to the out-of-box templates, App Engine Studio Administrators can configure custom templates for their developers.

![](/images/image33.png)

These templates can be configured with pre-defined Data, Experiences, Logic and Automation, and Security features, based on common use cases across the organization.

![](/images/image34.jpeg)

Custom application templates can be created from existing applications, or from scratch. Once a template has been configured, make it available to developers by publishing it in App Engine Studio.

*For more information, see [[Product Documentation: Custom templates]](https://docs.servicenow.com/csh?topicname=work-custom-templates.html)*

[Back to top](#top){: .btn .btn-purple }

---

# How do I manage App Engine Studio properties and processes? {#how-do-i-manage-app-engine-studio-properties-and-processes}

**Manage applications created in App Engine Studio**

Details for applications created in App Engine Studio are accessible by navigating to **System Applications \My Company Applications.** Administrators can access the following custom application data: application files, version, scope, dependencies, roles, and navigation. Applications can be published to an update set, if needed.

**App Engine Studio Properties**

Administrators can manage the App Engine Studio application properties in App Engine Studio by navigating to **App Engine Studio \> Configuration \Properties.**

**Pipelines**

Pipelines dictate the deployment path for App Engine Studio applications from development to production.

To create or edit pipeline configurations, navigate to **App Engine Studio \Pipelines and Deployments \Pipelines.**

**Environments**

Define the environments used in deployment pipelines to move applications across an organization. To create or edit environments, navigate to **App Engine Studio \Pipelines and Deployments \> Environments.**

**Application Intake Process**

Refine the intake request form by modifying the related Service Catalog items and customize the application intake approval process by modifying the approval flow for the item.

*For more information, see [[Product Documentation: Service catalog items]](https://docs.servicenow.com/csh?topicname=c_IntroductionToCatalogItems.html)*
*For more information, see [[Product Documentation: Flows]](https://docs.servicenow.com/csh?topicname=flows.html)*

**Integrations and Spokes**

Manage integrations with third-party systems via IntegrationHub. Integration spokes can be downloaded from the ServiceNow Store and must be installed to connect to App Engine Studio.

*For more information, see [[Product Documentation: IntegrationHub]](https://docs.servicenow.com/csh?topicname=integrationhub.html)*

**Instance Scans**

Configure Instance Scan definitions to ensure adherence to application development and organizational best practices.

Instance Scan definitions are executed when App Engine Studio applications are promoted to the test instance and can also be
executed ad-hoc.

*For more information, see [[Product Documentation: Instance Scan]](https://docs.servicenow.com/csh?topicname=hs-landing-page.html)*

**Automated Test Framework (ATF)**

Automate testing activities by creating ATF suites and tests for custom applications.

At a minimum, simple regression tests should be required for all citizen-developed applications.

ATF suites and tests are executed when App Engine Studio applications are promoted to the test instance and can also be executed ad-hoc.

*For more information, see [[Product Documentation: Automated Test Framework (ATF)]](https://docs.servicenow.com/csh?topicname=automated-test-framework.html)*

[Back to top](#top){: .btn .btn-purple }

---

# FAQs {#faqs}

**Can applications be accessed from App Engine Studio to ServiceNow Studio, and vice-versa?**

Yes. Applications built in App Engine Studio are accessible from ServiceNow Studio.

All application configurations are captured in the application scope, regardless of the development studio the configurations are performed in.

There are several capabilities available in ServiceNow Studio that are not accessible from App Engine Studio, including business rules, client scripts, and notifications.

**Does App Engine Studio support domain separation?**

Domain separation is not supported for App Engine Studio. The domain field may exist on data tables, but there is no business logic to manage the data.

**Can App Engine Studio applications be integrated with other applications outside of ServiceNow?**

Yes, App Engine Studios can interact with third-party systems by leveraging IntegrationHub spokes / actions exposed through Flow Designer.

**How can I safely expose third-party integrations in App Engine Studio?**

Consider pre-configuring authorized sub-flows for application developers to use when sharing data with third-party systems instead of allowing App Engine Studio developers to access IntegrationHub actions via Flow Designer.

This way, developers are not directly accessing any third-party systems, and data is shared and presented in a consistent manner across all applications built in App Engine Studio.

**How are Deployment Requests created and managed?**

Deployment Requests are generated and assigned to App Engine Studio Administrators in the production instance when application developers submit an application for IT review.

**How to enable other applications to read data in the application's table(s)?**

Update the 'Application Access' property for each table in an application to make its data accessible to other applications.

**Are App Engine Studio applications built in a private application scope?**

Yes, each application is developed in its own scope.

**How do I upgrade the App Engine Studio application?**

Administrators can update the App Engine Studio application in the ServiceNow Store.

**How can I manage developers of varying experience and skill in App Engine Studio?**

Consider creating multiple development groups in App Engine Studio for developers of different skill levels. Leverage delegated development to modify group access to builder tools accordingly.

Experienced developers may have more freedom with App Engine Studio tools and features than low-code developers, who may have fewer permissions in the application.

**Can I integrate App Engine Studio with Source Control?**

Yes, application developers can integrate with a Git Source Control repository to save and manage multiple versions of an application from a sub-production instance.

*For more information, see:*

-   [*[Product Documentation: Source Control integration in App Engine Studio]*](https://docs.servicenow.com/csh?topicname=aes-source-control-integration.html)

-   [*[Home - ServiceNow Developers]*](https://developer.servicenow.com/)

**Can I turn off the automatic execution of ATF tests and Instance Scan definitions?**

No, unless a new flow is created and the 'Deployment Environment Type Flow' Decision Table \[**sys_decision**\] is updated to point to the new flow for environments with instance type of 'Testing'.

If the ATF system properties are not enabled in the testing instance as part of the guided setup, you will receive a warning during deployment, however the flow will continue.

If the out-of-box test suite is not modified, they will run but will also not affect the flow.

**Can I change the instance where ATF tests and Instance Scan definitions are executed?**

Yes, this can be accomplished by updating the 'Instance Type' value for an Environment record to 'Testing'. Alternatively, the decision table can be modified to make the decision for 'Instance Type = Staging' (for example) point to the Testing sub-flow.