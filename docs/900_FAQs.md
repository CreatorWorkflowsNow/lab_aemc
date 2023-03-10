---
layout: default
title: FAQs
nav_order: 900
---

# FAQs
{: .no_toc }
{: .d-inline-block }
Published 3/10/23
{: .label .label-green }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Can applications be accessed from App Engine Studio to ServiceNow Studio, and vice-versa?
Yes. Applications built in App Engine Studio are accessible from ServiceNow Studio.

All application configurations are captured in the application scope, regardless of the development studio the configurations are performed in.

There are several capabilities available in ServiceNow Studio that are not accessible from App Engine Studio, including business rules, client scripts, and notifications. 

## Does App Engine Studio support domain separation?
Domain separation is not supported for App Engine Studio. The domain field may exist on data tables, but there is no business logic to manage the data.

## Can App Engine Studio applications be integrated with other applications outside of ServiceNow?
Yes, App Engine Studios can interact with third-party systems by leveraging IntegrationHub spokes / actions exposed through Flow Designer.

## How can I safely expose third-party integrations in App Engine Studio?
Consider pre-configuring authorized sub-flows for application developers to use when sharing data with third-party systems instead of allowing App Engine Studio developers to access IntegrationHub actions via Flow Designer.

This way, developers are not directly accessing any third-party systems, and data is shared and presented in a consistent manner across all applications built in App Engine Studio.

## How are Deployment Requests created and managed?
Deployment Requests are generated and assigned to App Engine Studio Administrators in the production instance when application developers submit an application for IT review.

## How to enable other applications to read data in the application’s table(s)?
Update the ‘Application Access’ property for each table in an application to make its data accessible to other applications.

## Are App Engine Studio applications built in a private application scope?
Yes, each application is developed in its own scope.

## How do I upgrade the App Engine Studio application?
Administrators can update the App Engine Studio application in the ServiceNow Store. 

## How can I manage developers of varying experience and skill in App Engine Studio?
Consider creating multiple development groups in App Engine Studio for developers of different skill levels. Leverage delegated development to modify group access to builder tools accordingly.

Experienced developers may have more freedom with App Engine Studio tools and features than low-code developers, who may have fewer permissions in the application.

## Can I integrate App Engine Studio with Source Control?
Yes, application developers can integrate with a Git Source Control repository to save and manage multiple versions of an application from a sub-production instance.

For more information, see:
• Product Documentation: Source Control integration in App Engine Studio
• Home - ServiceNow Developers

## Can I turn off the automatic execution of ATF tests and Instance Scan definitions?
No, unless a new flow is created and the ‘Deployment Environment Type Flow’ Decision Table [sys_decision] is updated to point to the new flow for environments with instance  type of ‘Testing’.

If the ATF system properties are not enabled in the testing instance as part of the guided setup, you will receive a warning during deployment, however the flow will continue. 

If the out-of-box test suite is not modified, they will run but will also not affect the flow.

## Can I change the instance where ATF tests and Instance Scan definitions are executed?
Yes, this can be accomplished by updating the ‘Instance Type’ value for an Environment record to ‘Testing’. Alternatively, the decision table can be modified to make the decision for ‘Instance Type = Staging’ (for example) point to the Testing sub-flow.

## Cloning? 
If you plan on cloning your production instance to one or more sub-production instances, you must complete the following:
- Install all App Engine plugins on all instances prior to cloning
- Enable ATF and Instance Scan properties in your production instance. 

Additionally, the AEMC plugin must be installed on all instances to appropriately collect application and developer data on development. For more information, see [[Product Documentation: System clone]](https://docs.servicenow.com/csh?topicname=c_SystemClone.html)

Consider enabling and configuring Instance Scan properties in your production instance if you plan to clone.
