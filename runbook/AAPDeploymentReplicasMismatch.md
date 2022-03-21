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
