# AAPPodContainerTerminated

## Meaning

AAP Pod in ansible-automation-platform namespace has been in the terminated state for longer than 10 minutes.

## Impact

AAP Pod is Terminated which means AAP service performance is usually degrading.

## Diagnosis

To check the AAP Pod status, the Pod status is not `Running`, it should be `CrashLoopBackOff`, and check the AAP pod log if we can find some reason.

### Database is full 

We will find the following error log from automation-hub-worker Pod:

```
psycopg2.errors.ReadOnlySqlTransaction: cannot execute UPDATE in a read-only transaction
django.db.utils.InternalError: cannot execute UPDATE in a read-only transaction
```
Then we can follow these steps to resolve this issue:

1. Identify the issue due to disk space. Navigate to the Postgres database then click the monitoring tab and check the storage ( should be near 100% )
2. Navigate to the UI and raise the storage ( can only be doubled )

## Mitigation

The resolution depends on the particular issue reported in the logs.
