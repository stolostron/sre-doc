# AAPPodRestartingTooMuch

## Meaning

AAP Pod in ansible-automation-platform namespace restart more than 10 times over 10 minutes.

## Impact

The AAP Pod restarts too much which means we have some Pod that is going wrong. AAP service performance is usually degrading.

## Diagnosis

To check the AAP Pod `RESTARTS` field and events, it should have the reason for the Pod restarting, and check the AAP pod log if we can find some reason.

## Mitigation

The resolution depends on the particular issue reported in the logs.
