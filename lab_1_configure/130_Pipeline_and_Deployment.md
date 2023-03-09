---
layout: default
title: Pipeline and Deployment
parent: 1 | Configure
nav_order: 130
---

# Configure - Pipeline and Deployment
{: .no_toc }

*hello world*

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Overview

Once App Engine Studio Guided Setup has been completed, administrators must complete the Pipeline and Deployment Guided Setup activities.

Pipelines enable you to automate the propagation and installation of your applications from one instance to another. Pipelines are powered by the ServiceNow CI / CD spoke, which enables you to automate processes such as publishing applications to the application repository, installing them on target instances, and running ATF tests and/or instance scans.

Pipeline and Deployment Guided Setup activities do not sync across instances and Pipeline configuration activities are required on all instances (production and sub-production).

{: .note-title}
> (re)start here
>
> *The following steps will need to be completed for all instances in your lab environment*
>
> *This is the spot you will start over at for each environment*
> 
> *For the purpose of the lab, we recommend starting in Prod, then Test, then Dev*

{: .highlight}
If you do not have a Prod, then start with Test, then Dev. 

**To access the Pipeline and Deployment Guided Setup:**
- Click **All** 
- type **app engine**
- click **Guided Setup** in the Pipelines and Deployments section

![](../images/2023-03-07-15-05-18.png)

Click the green **Get Started** button in the top-right.

![](../images/2023-03-07-15-23-27.png)

Click **Get Started** in the **Configuring your production instance** section

![](../images/2023-03-07-15-22-52.png)

{: .important}
*Before beginning Pipelines and Deployment Studio Setup, ensure your application scope is set to '**Deployment Pipeline**'. If not, use the application picker to change the current session's scope.*

![](../images/2023-03-03-16-47-44.png)

# Configure your production instance

In the **production** instance, complete the following steps to configure environments and deployment pipelines to streamline your application deployment process*.

{: .warning}
Complete these tasks only if you are logged into your production instance.

## Install 'Deployment Pipeline' plugin in production instance

{: .important }
> This has already been installed for you on the Lab instance. 

For future reference, the name of the Deployment Pipeline plugin is ***com.snc.deployment-pipeline**. 

## **Configure credentials in production instance**

Credentials allow your production instance to communicate with sub-production instances.

In production, navigate to **Connections & Credentials** >>  **Connection & Credential Aliases**.

{: .important}
Only users assigned the **admin** role can create and update Credential Alias records.

![](../images/2023-03-07-15-28-59.png)

Click the purple **New** button in the top-right to create a new Credential Alias record. 

![](../images/2023-03-07-15-38-10.png)

Set the **Type** to **Credential**.

![](../images/2023-03-07-15-37-39.png)

Set the **Name** to '*Pipeline Credentials*'

![](../images/2023-03-08-14-14-44.png)


---
{: .important}
Old data below here

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

{: .note}
Ensure that the controller instance was configured on all sub-production instances that are part of a pipeline!

[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

[PREVIOUS]: ../120_App_Engine
[NEXT]: ../140_App_Intake