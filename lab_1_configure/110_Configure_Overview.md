---
layout: default
title: Overview
parent: 1 | Configure
nav_order: 110
---

# Configuration Overview
{: .no_toc }

[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

---
## Below is a basic diagram outlining the steps needed to complete to have a working App Engine Management Center.

{: .note}
The install steps in the diagram were completed for you as part of the Lab setup. 

![](../images/2023-03-03-16-11-12.png)

***\*\*** Repeat steps across all sub-production instances, as necessary*

{: .note}
> If you plan on cloning your production instance to one or more sub-production instances, you must complete the following:
> - Install all App Engine plugins on all instances prior to cloning
> - Enable ATF and Instance Scan properties in your production instance. 
> 
> Additionally, the AEMC plugin must be installed on all instances to appropriately collect application and developer data on development. For more information, see [[Product Documentation: System clone]](https://docs.servicenow.com/csh?topicname=c_SystemClone.html)

The App Engine Studio bundle has three Guided Setup modules to assist in configuration:

- **App Engine Studio Guided Setup**
- **Pipeline and Deployment Guided Setup**
- **Application Intake Guided Setup**

We will review the steps contained in the Guided Setups over the new few lab sections.

[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

[PREVIOUS]: ../
[NEXT]: ../120_App_Engine