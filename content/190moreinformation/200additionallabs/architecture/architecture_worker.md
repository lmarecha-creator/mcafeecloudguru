---
title: "Conclusion"
date: 2020-02-24
weight: 60
---

### What did we do? ###

1. We linked our Azure environment to our MVISION Cloud tenant to run two different types of security scans. This included Cloud Security Posture Management (CSPM) scans against the Azure environment as a whole, as well as the AKS cluster. 

2. We configured a number of policies associated with those scans, including numerous Container Security policies

3. We configured a Container vulnerability policy and run a scan agains Container images in ACR.

4. After identifying issues, we went back into the Azure environment and fixed them via Azure Cloud shell CLI. This would be very indicative of what your DevOps team would need to do!

5. Finally, we rescanned the environment to show through reporting a reduction of Open incidents.
