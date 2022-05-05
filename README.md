# VICGOV - Azure Active Directory Roles Report
## 1. Introduction
### 1.1	Overview

A number of challenges arise when managing AAD roles across multiple tenants, Hosting Services team have been working to make this process easier to maintain with less administrative overhead.

This document is intended to provide a high level overview of workflow on how the automation notifies the admins with Azure AD roles assigned to all staff in VICGOV.

Included in this report is a step by step detailed guide around where to look for troubleshooting.

## 2 O365 Process Reports (CIS Benchmark)
- Priority: 1
- Description: You should review non-global administrator role group assignments at least every week
- Rationale: While these roles are less powerful than a global admin, they do grant special privileges that can be used illicitly. If you see something unusual, contact the user to confirm it is a legitimate need.
- Owners: Tier 0
- Ref: E3_L1


## 3 Logical Architecture
### 3.1	Logical System Component Overview
![Figure 1: Logical Architecture Overview](./.images/workflow.png)
1. Scheduled Job @ 7am on Friday.
2. Function retreives the secrets from the Keyvault.
3. Queries AAD for validating managed identity.
4. Checks AAD for the assigned roles.
5. The notification email gets sent via logic apps with the report attached.
