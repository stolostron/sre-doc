**Alert Name:** AAPPodNotReady

**Description:** AAP Pod in ansible-automation-platform namespace has been in a non-ready state for longer than 15 minutes

**Severity:** critical

**Service:** Ansible Automation Platform

**Dependencies:** n/a

**Troubleshooting:** To check the AAP Pod status, the Pod status is not `Running`, it should be `Pending` or `Unknown` or `Failed`

**Related Alerts:**
- AAPDeploymentReplicasMismatch
- AAPPodFrequentlyRestarting
- AAPPodRestartingTooMuch

**Root Cause:**
1. Database is full, so write is blocked. We will found the following error log from automation-hub-worker Pod:
```
psycopg2.errors.ReadOnlySqlTransaction: cannot execute UPDATE in a read-only transaction
django.db.utils.InternalError: cannot execute UPDATE in a read-only transaction
```

**Resolution:**
- Root Cause 1
    - Step 1: Identify issue is due to disk space. Navigate to the Postgres database then click the monitoring tab and check the storage(should be near 100%)
    - Step 2: Navigate to the UI and raise the storage(can only be doubled)

**Dashboards:** n/a

**Related Links:** n/a
