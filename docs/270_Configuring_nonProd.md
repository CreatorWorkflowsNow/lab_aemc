---
layout: default
title: Configure non-Prod
nav_order: 270
parent: Pipelines & Deployments
has_children: false
permalink: /docs/Configure_nonProd
---

# Configure non-Prod

# Environment setup

{: .highlight}
> *Each step below will need to be completed on each Subproduction instance in your environment.*

| 1) Log in to the environment |
| 2) Click 'All', Type 'pipeline' | ![](../assets/images/2023-03-12-21-33-52.png)
| 3) Click 'Guided Setup' | ![](../assets/images/2023-03-12-21-33-52.png)
| 4) In the section '*Configuring your non-production instances*', click **Get Started** | ![](../assets/images/2023-03-13-10-21-23.png)
| 5) In the section '*Configure the controller instance*', click **Configure** | ![](../assets/images/2023-03-13-10-22-34.png)
| 6) Click **New** | ![](../assets/images/2023-03-13-10-24-26.png)
| 7) Complete the form using the information below. | ![](../assets/images/2023-03-13-10-31-06.png)

| Field | Value |
|:---|:---|
| Name | ```Prod``` |
| Instance Type| ```Production``` |
| Instance URL | ```The full URL of your Prod Lab instance (Ex. https://your-lab-123.service-now.com)``` |
| Instance credential | ```sn_deploy_pipeline.Pipeline_Credentials``` |
| Is Controller? | ```Leave unchecked``` |
| Instance Id | ```*See instructions link below on how to get stats.do page*``` |

{: .warning}
***Complete the next few steps in a new browser tab so you do not lose your place***

**In your new browser tab**

| 8) Navigate to your **Prod** instance
| 9) Click **All** 
| 10) Type ```stats.do``` | ![](../assets/images/2023-03-10-16-31-47.png) 
| 11) Hit Enter
| 12) Select and copy the value for *Instance ID* | ![](../assets/images/2023-03-09-15-39-10.png)

{: .warning}
***Close this browser tab and switch back to your previous browser tab*** 

| 13) Paste the *Instance ID* value into the *Instance ID* field and click **Validate**. | ![](../assets/images/2023-03-12-16-58-04.png)

| ![](../assets/images/2023-03-09-15-50-27.png)

| You should see a blue message that says "*The controller environment was validated successfully*". | ![](../assets/images/2023-03-12-17-05-44.png)

{: .warning}
> *If you see a red error message*
> ![](../assets/images/2023-03-09-15-53-40.png)
>
> *Then you will need to do the following:*
> - Open a new browser tab to Prod
> - Set the password for **pipeline_user**
> - Update the Credential records for **pipeline_user**
> - Attempt Validation again

| 14) Click **Submit** to finish creating the '*Prod*' environment record | ![](../assets/images/2023-03-12-16-59-46.png)

{: .highlight}
> If you get a message like below that says '*This is an invalid URL.*', click 'X' in the top right and close the modal. 
>
> That error can be safely ignored.

| ![](/assets/images/2023-03-13-10-48-10.png)
