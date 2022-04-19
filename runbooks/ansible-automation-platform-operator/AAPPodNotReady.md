# AAPPodNotReady

## Meaning

AAP Pod in ansible-automation-platform namespace has been in a non-ready state for longer than 15 minutes.

## Impact

AAP Pod is not ready which means AAP service performance is usually degrading.

## Diagnosis

To check the AAP Pod status, the Pod status is not `Running`, it should be `Pending` or `Unknown` or `Failed`, and check the AAP pod log if we can find some reason.

### Database is full 

We will find the following error log from automation-hub-worker Pod:

```
psycopg2.errors.ReadOnlySqlTransaction: cannot execute UPDATE in a read-only transaction
django.db.utils.InternalError: cannot execute UPDATE in a read-only transaction
```
Then we can follow these steps to resolve this issue:

1. Identify the issue due to disk space. Navigate to the Postgres database then click the monitoring tab and check the storage ( should be near 100% ).
2. Navigate to the UI and raise the storage ( can only be doubled ).

## Mitigation

The resolution depends on the particular issue reported in the logs.
