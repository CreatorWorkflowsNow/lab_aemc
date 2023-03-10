---
layout: default
title: 3. AES Admin in Prod
nav_order: 240
parent: Configure Prod
grand_parent: Pipelines & Deployments
permalink: /docs/configure-prod-aes-admin
---

{: .d-inline-block }
# Configure Prod AES Admin Group
{: .d-inline-block }
Published 3/13/2023
{: .label .label-green }

[Previous][PREV]{: .btn .mr-2 .fs-2}
[Next][NEXT]{: .btn .btn-purple .fs-2}

# Add users to the App Engine Studio Administrators group

{: .note}
*Configure App Engine Studio administrator group membership in the **production** instance to manage application intake and deployment requests.*

*Ensure the group membership in **production** is consistent with the App Engine Studio administrators identified in the **development** instance.*

*Group membership does not sync between environments and must be updated in both production and development.*

{: .warning}
If group membership is empty in the production instance, or if the Deployment Pipeline plugin is not installed, the system will refer to App Engine Studio Administrator group membership in the development instance.

{: .warning}
>This section is to be completed in your **production** instance where AEMC will be running.

| 1) In the '*Add users to the App Engine Admins group*' section, click **Configure** | ![](../assets/images/2023-03-12-20-57-36.png)
| 2) In the 'Group Members' related list, click **Edit...**| ![](../assets/images/2023-03-12-21-00-01.png)
| 3) Search for **Jayne Nigel**, move her to the right side of the list collector, and click **Save**. | ![](../assets/images/2023-03-12-21-05-49.png)
| 4) Click 'X' to exit the modal. | ![](../assets/images/2023-03-12-21-07-00.png)
| 5) In the '*Add users to the App Engine Admins group*' section, click **Complete** | ![](../assets/images/2023-03-12-21-07-42.png)
| 6) Click '*Pipelines and Deployments Guided Setup*' at the top of the page |![](../assets/images/2023-03-12-21-08-59.png)

**Congratulations! Your Production instance is configure for App Engine!**

**Next, you will configure your non-production instances. These are also sometimes referred to as Subproduction.**

---

[Previous][PREV]{: .btn .mr-2 .fs-2}
[Next][NEXT]{: .btn .btn-purple .fs-2}

[PREV]: /lab_aemc/docs/configure-prod-pipeline
[NEXT]: /lab_aemc/docs/configure-non-prod