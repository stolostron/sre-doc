# AAPStatefulSetReplicasMismatch

## Meaning

AAP StatefulSet in ansible-automation-platform namespace actual number of replicas is inconsistent with the set number of replicas over 5 minutes

## Impact

The actual number of replicas is inconsistent with the set number of replicas which means we have some Pod is terminated. AAP service performance is usually degrading.

## Diagnosis

To check the AAP Pod status, the Pod status is not `Running`, it should be `Pending` or `Unknown` or `Failed`, and check the AAP pod log if we can find some reason.

## Mitigation

The resolution depends on the particular issue reported in the logs.
