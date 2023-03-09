---
layout: default
title: 1 | Configure
nav_order: 100
has_children: true
has_toc: false
---

# Configure

Lab 1 Configure contains three sections.  

It is recommended to complete them in the order provided in the Lab Guide. 

{: .note}
> If you plan on cloning your production instance to one or more sub-production instances, you must complete the following:
> - Install all App Engine plugins on all instances prior to cloning
> - Enable ATF and Instance Scan properties in your production instance. 
> 
> Additionally, the AEMC plugin must be installed on all instances to appropriately collect application and developer data on development. For more information, see [[Product Documentation: System clone]](https://docs.servicenow.com/csh?topicname=c_SystemClone.html)

Below is a basic diagram outlining the steps needed to complete to have a working App Engine Management Center.


![](./images/2023-03-03-16-11-12.png)

{: .note}
The install steps in the diagram were completed for you as part of the Lab setup. 

| [App Engine Studio Guided Setup][AppEngineStudio]{: .btn .btn-purple } | Configure foundational application components and provision initial user access |
| [Pipeline and Deployment Guided Setup][Pipeline]{: .btn .btn-purple } | Configure pipelines to deploy applications across instances with confidence |
| [Application Intake Guided Setup][AppIntake]{: .btn .btn-purple } | Configure application intake catalog item and process to enable business users to submit application requests from an existing service portal |

[AppEngineStudio]: ./120_App_Engine
[Pipeline]: ./130_Pipeline_and_Deployment
[AppIntake]: ./140_App_Intake