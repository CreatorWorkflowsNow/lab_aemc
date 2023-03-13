---
layout: default
title: Pipeline
nav_order: 230
parent: Configure Prod
grand_parent: Pipelines & Deployments
permalink: /docs/configure-prod-pipeline
---


# Configure Prod Pipeline
*Part of: Configuring Prod*
{: .fs-4 .fw-300 }

{: .d-inline-block }
WORK IN PROGRESS
{: .label .label-yellow }

{: .d-inline-block }
80% complete
{: .label .label-red }

<!-->
{: .important}
> *Before beginning Pipelines and Deployment Setup, ensure your application scope is set to '**Deployment Pipeline**'.* | ![](../assets/images/2023-03-03-16-47-44.png)
-->
Pipelines enable you to automate the propagation and installation of your applications from one instance to another. Pipelines are powered by the [ServiceNow CI / CD spoke](https://docs.servicenow.com/csh?topicname=cicd-spoke-1.html&version=latest), which enables you to automate processes such as publishing applications to the [application repository](https://docs.servicenow.com/csh?topicname=app-repo.html&version=latest), installing them on target instances, and running [ATF tests](https://docs.servicenow.com/csh?topicname=automated-test-framework.html&version=latest) and/or [instance scans](https://docs.servicenow.com/csh?topicname=hs-landing-page.html&version=latest).

Pipeline and Deployment Setup activities do not sync across instances and Pipeline configuration activities are required on all instances (production and sub-production).

In the **production** instance, complete the following steps to configure environments and deployment pipelines to streamline your application deployment process.

{: .highlight}
> The 'Deployment Pipeline' plugin has already been installed for you in this Lab. 
>
> For future reference, the name of the Deployment Pipeline plugin is ```com.snc.deployment-pipeline```
>

## Configure pipelines in production

*A pipeline defines the path an application takes from the development to production environments and allows administrators to quickly move applications across instances.*

*Set up and configure your pipeline by specifying the environments to include along with their position in the pipeline.*

| 1) In the '*Configure piplines*' section click **Configure**. | ![](../assets/images/2023-03-12-17-25-15.png)
| 2) Click **New** | ![](../assets/images/2023-03-12-17-27-31.png)

| 3) Complete the form as below.  Click Submit when complete.

| Field | Value 
|:---|:---
| Name | ```My first pipeline``` 
| Pipeline Type | ```Application Deployment```
| Source Environment | ```Dev```
| Active | Checked

{: .note}
> *Once a pipeline has been created, use the **Pipeline Environments Order** Related List on the Pipeline record to configure the instance order for the pipeline. 
> 
> Create a record in the related list for all instances ***except*** the development instance and specify the environment's order within the pipeline.*
>
> *Application movement across pipelines is dictated by the order of the environments in the Pipeline Environment Order related list, and applications are promoted based on ascending 'Order' values.*
>
> *Be sure the environment order is consistent with the defined instance strategy. The production instance should have the highest 'Order' value *(i.e., Testing: 100, Staging: 200, Production: 300).*
>

| 4) Click **My first pipeline** to open the record | ![](../assets/images/2023-03-12-17-31-52.png)
| 5) In the *Pipeline Environments Order* related list, Click** **New** | ![](../assets/images/2023-03-12-17-32-31.png)

| 6) Complete the form as below.  Click Submit when complete.


| Field | Value 
|:---|:---
| Pipeline | ```My first pipeline``` 
| Environment | ```Production```
| Order | ```100```

***Note:** Since the development environment is already identified as the 'Source Environment' on the Pipeline record, a Pipeline Environment Order related record is not required*

| 7) Click 'X' to close the modal | ![](../assets/images/2023-03-12-17-34-44.png)
| 8) In the '*Configure Pipelines*' section click **Mark as Complete** | ![](../assets/images/2023-03-12-17-35-33.png) 

Congratulations! You have created a new **Pipeline** in your Prod environment. 

Next, we will...

---

{: .note}
*For more information, see [[Product Documentation: Create a pipeline]](https://docs.servicenow.com/csh?topicname=create-pipeline.html)*

--

{: .warning}
> Old data below here

| ![](/assets/images/image21.jpeg)


**Pipeline Environment Orders**



2.  **[Configure sub-production instances]**

Follow the steps below to install the 'Deployment Pipeline' plugin in each [sub-] [production] instance.

Once installed, you will be required to configure an environment record in each instance which points to the production (controller) instance.

You will also enable the system properties that will allow the Automated Test Framework (ATF) suite to run during the deployment process.

**Complete these tasks only if you are logged into a sub-production instance.**

a.  **Install the 'Deployment Pipeline' plugin in each sub-production instance**

To install the Deployment Pipeline plugin, (*com.snc.deployment-pipeline)*, login to any sub-production instance and navigate to **System Definition \Plugins.**

Use the search criteria to find the application. Click **Install**.

Repeat and install the Deployment Pipeline plugin in each sub-production instance.

| ![](/assets/images/image22.png)

***Note:** If you have already installed the App Engine Studio bundle in the development instance and promoted up to production, skip this step*

**Repeat this task on each sub-production instance that will be part of a pipeline**

b.  **Configure credentials in each sub-production instance**

In each sub-production instance, create a Credential Alias record and associate the Credentials for the production instance.

Navigate to Connections & Credentials \Connection & Credential Aliases.

Based on the credential information, take the appropriate approach in configuring Credential Alias records:

| ![](/assets/images/image17.png)


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

| ![](/assets/images/image23.jpeg)

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

[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

---
Additional Notes

{: .note}
> *Set up and configure the environments that will be included within your pipelines. These will be referenced when building your pipelines.*
> 
> *Your production instance is where your pipeline configurations reside and will be your controller instance.*
> 
> *The 'Is Controller?' box will be **checked** on your production instance only. This box will be **unchecked** for all sub-production Environment records.*
>
> If you have **more than one** Production environment, then AEMC will only be the controller on a single instance for all of your other Prods. 


[PREVIOUS]: /docs/configure-prod-environments
[NEXT]: /docs/configure-prod-aes-admin