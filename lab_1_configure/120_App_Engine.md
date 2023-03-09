---
layout: default
title: App Engine Studio
parent: 1 | Configure
nav_order: 120
---

# Configure - App Engine Studio
{: .no_toc }
{: .d-inline-block }
Ready for review
{: .label .label-green }

*In this lab, we will review and update App Engine Studio developer access to builder tools during development.*

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Log in to Dev

Log in to your **Dev** instance. 

{: .warning}
Be sure your application scope is set to **App Engine Studio**. If it is not, use the application picker to change the current session's scope.

![](../images/2023-03-03-16-39-04.png)

Navigate to **All**, then type **App Engine**, then look for **Configuration** -> "**Guided Setup**.  

Click on **Guided Setup**. 

![](../images/2023-03-06-16-55-44.png)

Click on "**Get** **Started**"

![](../images/2023-03-06-17-01-22.png)

---
# Review and set up tooling

Click on **Get Started** in the **Review and setup tooling** section

![](../images/2023-03-06-17-00-41.png)

---
## Connect Spokes

Click on **Skip** in the **Connect Spokes** Section

![](../images/2023-03-06-17-05-43.png)

{: .note}
*We are skipping **Connect Spokes** for this lab. In that section, you would configure credentials to different services to that they can be leveraged by App Engine Users building applications.*

---
## Flow Designer access settings

Click **Configure** in the **Review Flow Designer access settings** section.

![](../images/2023-03-06-17-08-18.png)

**Things to consider**

Here you would want to review and update App Engine Studio developer access settings to Flow Designer Resources and update as necessary.

Developers can leverage Flow Designer capabilities while creating logic and automation for custom applications.

Consider restricting developer access to Flow Designer Resources using content filtering for Flow Designer. This allows administrators to manage access to Flow Designer resources and specify which features App Engine Studio users can leverage while building applications.


![](../images/2023-03-06-17-09-26.png)

{: .note}
> For the purposes of this lab, we are only reviewing where to manage the Flow Designer access settings.
>
> *This step is not required as part of the initial application setup.*

Flow Designer access from App Engine Studio can be updated later to provide developers the editing capabilities that best suit their experience and needs.

{: .highlight}
*For more information on Flow Designer resources, see [[Product Documentation: Content Filtering for Flow Designer]](https://docs.servicenow.com/csh?topicname=content-filtering-flow-designer.html)*

When you are done reviewing the Flow Designer access settings, close out the modal, then click **Mark as Complete**.

![](../images/2023-03-06-17-15-51.png)

![](../images/2023-03-06-17-15-26.png)

You should notice that the % Complete has increased on the page. 

![](../images/2023-03-06-17-17-15.png)

---
## Review Service Catalog access settings

Click **Configure** on **Review Service Catalog access settings**

![](../images/2023-03-06-17-18-08.png)

You should review App Engine Studio developer access to the Catalog Builder tool’s catalog item templates and catalogs / categories, and update access as necessary.

The goal of this lab is to ensure you are aware of this information and where to configure.  No configuration of the Service Catalog access setting is necessary for the lab. 

By default, App Engine Studio developers can leverage catalog templates to quickly create record producers or catalog items. Developers can also publish catalog items to any catalog. If you wish to limit access to templates or restrict publishing access to catalogs or categories, update the access accordingly in Catalog Builder.

{: .highlight}
*For more information on managing the Catalog Builder, see [[Product Documentation: Set up the catalog builder]](https://docs.servicenow.com/csh?topicname=set-up-cat-builder.html&version=latest)*

Click **Mark as Complete** on the **Review Service Catalog access settings** section

![](../images/2023-03-06-17-29-45.png)

---
## Set up an instance scan cadence in Health Center

Click **Configure** in the section **Set up an instance scan cadence in Health Center**

![](../images/2023-03-06-17-31-15.png)

{: .note}
> For the purposes of this lab, we are only reviewing where to manage the Instance Scan definitions 
>
> Work with your Platform Adminstrator on an overall Instance Scan strategy for Subproduction environments. 

![](../images/2023-03-06-17-31-52.png)

Deploy custom applications with confidence by setting up Instance Scan definitions to monitor instance health throughout the deployment process. Instance scans interrogate your instance for configurations and health issues, allowing administrators an opportunity to address best practices and to avoid similar configuration issues in the future.

Instance Scan definitions are executed automatically when App Engine Studio applications are promoted to the **Testing** instance. Instance Scan results will be logged in the Notes section of the Deployment Request record.

The App Engine Studio application does not ship with any out-of-box Instance Scan definitions (however a few Instance Scan definitions are installed with the Deployment Pipeline plugin to run basic performance checks).

Work with professional ServiceNow developers to configure Instance Scan definitions and enforce best practices in your environments.

![](../images/2023-03-03-16-42-38.png)

**Enable and configure Instance Scan properties in your production instance if you plan to clone!**

{: .highlight}
*For more information on managing instance health scans, see [[Product Documentation: Instance Scan]](https://docs.servicenow.com/csh?topicname=hs-landing-page.html)*

Click **Mark as Complete** on the **Set up an instance scan cadence in Health Center**

![](../images/2023-03-06-17-35-47.png)

---

# Set up user access

Click the gray circle on the left hand side of the page below the green check mark.  

It should say **Set up user access** when you hover over it. 

![](../images/2023-03-06-17-36-57.png)

Click **Get Started** in the **Set up user access** section

![](../images/2023-03-06-17-38-21.png)

## Set up admin group

Configure App Engine Studio administrator group membership in the [development] instance to manage development activities that occur in the development environment.

While development activities will be managed in the [development] instance, administrators manage application intake, collaboration, and deployment requests in [production].

{: .note}
*Group membership does not sync across instances, therefore App Engine Studio administrator group membership will also need to be provisioned in the [production] instance as part of the Pipelines and Deployment or Application Intake Guided Setup activities*

Click **Configure** in the **Set up admin group** section

![](../images/2023-03-07-12-13-00.png)

Click **Edit...** on the **Group Members** tab

![](../images/2023-03-07-12-16-02.png)

Move **Jayne Nigel** to the right hand side and click Save like in the image below.

![](../images/2023-03-07_14-07-09.gif)

{: .important}
> Jayne will play the part of our App Engine Admin during the lab today.

Click the "Group = App Engine Admins" filter on the **Group Members (1)** related list to refresh the list. 

![](../images/2023-03-07-14-22-13.png)

You should see **Jayne Nigel** appear in the **User** column. 

After that click the "X" in the top right corner to close the modal. 

![](../images/2023-03-07-14-13-17.png)

Next to **Set up admin group** click "Mark as Complete" then next to **Grant access to your current developers** click "Mark as Complete".

![](../images/2023-03-07-14-17-31.png)

{: .highlight}
>We are skipping **Grant access to your current developers** as it has you create new users from scratch.  While this may work for some organizations, most of the time the user data is already synced from a Production environment. 
>

Click **Configure** next to **Grant access to other users**

![](../images/2023-03-07-14-23-55.png)

Click **Edit** on the **Group Members** related list. 

![](../images/2023-03-07-14-25-01.png)

Move **Abel Tuter** to the right hand side and click **Save**. 

The purpose of this step is to add users to the group "App Engine Studio Users" which will grant them access to App Engine Studio via the role **sn_app_eng_studio.user**.

{: .important}
> In the next section, we will learn how to set up an Intake process for users that want to apply to be an **App Engine Studio User**. 

Click the **X** in the top right of the modal to close it. 

![](../images/2023-03-07-14-28-16.png)

Next to **Grant access to other users** click **Mark as Complete**.

![](../images/2023-03-07-14-46-12.png)

That completes the App Engine Studio Guided Setup portion of the lab. 

In a real world scenario, you would also want to consider all or some of the above settings in your overall Platform cloning strategy.  


[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

[PREVIOUS]: ../
[NEXT]: ../130_Pipeline_and_Deployment