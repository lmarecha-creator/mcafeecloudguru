---
title: "Cloud Security Posture Management (CSPM) Policies"
date: 2020-02-24
weight: 70
---

For the first Security Scan, we will be performing Cloud Security Posture Management (CSPM or Config Audit) against both the Azure environment as a whole and the Azure Kubernetes Service (AKS).

Hover over POLICY at the top and select CONFIGURATION AUDIT.

![cspm1](/images/mvcscan/cspmpolicy01.png?classes=border,shadow)

By default, MVC enables all the CSPM policies to provide customers a comprehensive baseline to their IaaS posture. For this lab, we only want to test a few to start.

Click the check box at the top-left of the list to select all the CSPM policies. Next, click the ACTION button at the top-right and choose DEACTIVATE POLICIES. Confirm your selection.

![cspm2](/images/mvcscan/cspmpolicy02.png?classes=border,shadow)

On the left hand side, expand the Policy Category section and choose "Container Security". Then select the checkbox above the list to select all the policies. Once all the Container Security policies are selected, click ACTIONS in the top right and choose activate.

![cspm3](/images/mvcscan/AKS-audit.png?classes=border,shadow)


