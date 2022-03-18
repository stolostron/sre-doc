**Alert Name:** AAPPodContainerTerminated

**Description:** AAP Pod in ansible-automation-platform namespace has been in terminated state for longer than 10 minutes

**Severity:** critical

**Service:** Ansible Automation Platform

**Dependencies:** n/a

**Troubleshooting:** To check the AAP Pod status, the Pod status is not `Running`, it should be `CrashLoopBackOff`

**Related Alerts:**
- AAPPodNotReady
- AAPPodRestartingTooMuch
- AAPPodFrequentlyRestarting

**Root Cause:**
1. Database is full, so write is blocked. We will found the following error log from automation-hub-worker Pod:
```
psycopg2.errors.ReadOnlySqlTransaction: cannot execute UPDATE in a read-only transaction
django.db.utils.InternalError: cannot execute UPDATE in a read-only transaction
```

**Resolution:**
- Root Cause 1
    - Step 1: Identify issue is due to disk space
    - Step 2: Navigate to the UI and raise the storage(can only be doubled)

**Dashboards:** n/a

**Related Links:** n/a
