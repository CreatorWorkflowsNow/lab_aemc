---
layout: default
title: Personas & Roles
parent: Pre-Req Info
nav_order: 10
---

# Personas and Roles
{: .no_toc }

[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

{: .highlight}
> This overview is for information purposes only. 
>
> No activity required.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
# System Administrator
## Responsibilities
- Install and configure App Engine Studio and dependencies
- Define Environments and configure Pipelines
- Provision App Engine Studio administrator group access 
- Upgrade the App Engine Studio application, when applicable
- Define guardrails for which App Engine Studio Administrators can approve or reject application intake requests 
- Collaborate with professional ServiceNow developers to create Instance Scan 
definitions for the platform
- Collaborate with App Engine Studio Administrator(s) to resolve application conflicts that arise on the platform

## Role required: 
- admin

# App Engine Studio Administrator
## Responsibilities
- Manage App Engine Studio processes and properties
- Review and approve / reject submitted application requests, based on intake guardrails defined by System Administrator
- Provision App Engine Studio user access
- Review submitted App Engine Studio applications 
- Manage Deployment Requests 
- Manage promotion of App Engine Studio applications across instances
- Execute ATF tests / suites in testing instanc
- Ensure Instance Scan is run with proper definitions 
- Collaborate with System Administrator to resolve application conflicts that arise on 
the platform

## Role(s) required:
- sn_app_eng_studio.admin
- atf_test_designer
- scan_admin

# Professional ServiceNow Developer
## Responsibilities
- Build and test applications in ServiceNow Studio and App Engine Studio
- Collaborate with citizen developers, on an as-needed basis, to deliver applications in App Engine Studio, including:
  - Ensure application development and organizational best practices are followed by citizen developers
  - Assist in review and testing of submitted App Engine Studio applications
- Build complex configurations involving UI Builder, Mobile App Builder, Flow Designer, or other builder tools
- Create ATF tests / suites for applications
- Collaborate with system administrator to create Instance Scan definitions for the 
platform

## Role(s) required:
- delegated_developer
- sn_app_eng_studio.user
- atf_test_admin
- scan_admin


# Low-Code / Citizen Developer
## Responsibilities
- Submit requests for new custom applications to build in App Engine Studio
- Understand ServiceNow and application development best practices
- Build and test applications in App Engine Studio
- Submit developed App Engine Studio applications for IT review
- Maintain and modify the application during its lifecycle if determined during the intake process

## Role required:
- sn_app_eng_studio.user

[Previous][PREVIOUS]{: .btn .mr-4 }
[Next][NEXT]{: .btn .btn-purple }

[PREVIOUS]: ../10_AES_Overview
[NEXT]: ../../lab_1_Configure_AES