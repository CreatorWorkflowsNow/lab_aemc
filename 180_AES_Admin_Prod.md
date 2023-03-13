---
layout: default
title: AES Admin in Prod
nav_order: 180
---

# Configure Pipeline
*Part of: Configuring your production instance*
{: .fs-4 .fw-300 }

{: .d-inline-block }
WORK IN PROGRESS
{: .label .label-yellow }

{: .d-inline-block }
5% complete
{: .label .label-red }


# Add users to the App Engine Studio Administrators group

{: .note}
*Configure App Engine Studio administrator group membership in the **production** instance to manage application intake and deployment requests.*

*Ensure the group membership in **production** is consistent with the App Engine Studio administrators identified in the **development** instance.*

*Group membership does not sync between environments and must be updated in both production and development.*

{: .warning}
If group membership is empty in the production instance, or if the Deployment Pipeline plugin is not installed, the system will refer to App Engine Studio Administrator group membership in the development instance.

{: .warning}
>This section is to be completed in your **production** instance where AEMC will be running.

