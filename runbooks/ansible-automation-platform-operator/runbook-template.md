Following this template to write a runbook via [Markdown formatting](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#ignoring-markdown-formatting):

```markdown
**Alert Name:** AAPDeploymentReplicasMismatch

**Description:** AAP Deployment in ansible-automation-platform namespace actual number of replicas is inconsistent with the set number of replicas

**Severity:** warning

**Service:** Ansible Automation Platform

**Dependencies:** n/a

**Troubleshooting:** To check the AAP Deployment status, the actual number of replicas is not equal to the set number of replicas

**Related Alerts:**
- AAPPodNotReady

**Root Cause:**
1. Can not create the Pod due to the Service Account is not exist

**Resolution:**
- Root Cause 1
    - Step 1: Log in to the managed cluster
    - Step 2: Create the Service Account for the Deployment
    - Step 3: Check the Deployment status to ensure that the actual number of replicas is consistent with the set number of replicas

**Dashboards:** n/a

**Related Links:** n/a
```

## Field Definition

Field | Description
:---: | :---
Alert Name | Alert name
Description | Alert description
Severity | Alert severity
Service | Which service is belong to this alert
Dependencies | Alert dependency
Troubleshooting | Some steps to check and verify this alert
Related Alerts | Some related alerts
Root Cause | Alert root cause
Resolution | Some steps to fix this alert according to special root cause
Dashboard | Alert related dashboard link
Related Links | Some links are useful for this alert
