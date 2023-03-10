---
layout: default
title: Install Requirements
nav_order: 130
---

# Install Requirements
{: .no_toc }
{: .d-inline-block }
Published 3/10/23
{: .label .label-green }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

{: .highlight}
> Install requirements for App Engine are provided for information purposes only. 
>
> The install steps were completed for you as part of the Lab setup. 
>
> We **highly** encourage reviewing the information below before attempting a live install. 
>
> [I'm brave... Skip to next lab][NEXT]{: .btn .btn-purple }

---

Before installing App Engine Studio, review all platform requirements and define an organizational instance strategy to prepare for successful installation and configuration.

# Platform requirements
- App Engine license required
  -	Contact your ServiceNow Account Manager for additional information on App Engine, or see [ServiceNow App Engine](https://www.servicenow.com/products/now-platform-app-engine.html)
- **admin** role is required in all instances to install App Engine applications from the ServiceNow Store

# Define instance strategy
When defining the instance strategy for App Engine Studio, it is recommended to leverage one production instance and at least two sub-production instances – however App Engine Studio can support any number of sub-production instances as part of an instance strategy.

Applications are deployed to the production instance once developed and successfully tested in sub-production instances. One sub-production instance will serve as the development environment, and the other as the test environment.

If your organization uses sandbox or staging environments in addition to test and development, they can be incorporated to the instance strategy accordingly based on organizational needs.

![](../images/2023-03-03-15-28-00.png)

*Example instance strategy with one production instance and three sub-production instances*

Sub-production instances that are most similarly configured to your production instance are the best candidates for test and stage environments. This way, administrators can more accurately find issues that may arise if the application is deployed to production.

*For more information, see [[Product Documentation: Instance strategy for App Engine Studio]](https://docs.servicenow.com/csh?topicname=aes-instance-strategy.html)*

---

# Opt-in and manage entitlements

Before installing the application from the ServiceNow Store, verify the instance has valid ServiceNow entitlements.

In the ServiceNow Store, use the search criteria to find App Engine Studio.

![](../images/2023-03-03-15-31-33.png)
 
Click **Opt-in** and agree to the ServiceNow terms and conditions to verify entitlements.

Click **Manage Entitlements** and set the 'Entitlement Type' value to **Entitle all Instances** (*if you prefer to manually select which instances which will be affected, select Entitle Selected Instances).*

# Install App Engine applications

{: .highlight}
> App Engine Studio has already been installed for you in this lab. 
>
> No actual install required.

To install the App Engine Studio application (***com.snc.app-engine-studio***), login to your **development** instance and navigate to "System Applications" >> "All Available Applications" >> "All"

Use the search criteria to find the App Engine Studio application. Click **Install / Update All**.

![](../images/2023-03-03-15-31-55.png)

The App Engine Studio bundle will be installed in the development instance-- including the App Engine Studio application and all dependent applications.

---

To install the App Engine Management Center application (***sn_aemc***), login to your **production** instance and navigate to "System Applications" >> "All Available Applications" >> "**All**"

Use the search criteria to find the App Engine Management Center application. Click **Install / Update All**.

![](../images/2023-03-03-15-36-59.png)

Repeat this process on all instances for cloning purposes.

*For more information, see:*

-   [*[ServiceNow Store: Install a ServiceNow Product]*](https://store.servicenow.com/%24appstore.do%23!/store/help?article=KB0030186)

-   [*[Product Documentation: Install App Engine Studio]*](https://docs.servicenow.com/csh?topicname=install-aes.html)



[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

[PREVIOUS]: ../120_Personas_and_roles
[NEXT]: ../160_Configure_AES_in_Dev