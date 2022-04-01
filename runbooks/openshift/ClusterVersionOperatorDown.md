# ClusterVersionOperatorDown

## Meaning

This alert is triggered when cluster version operator has disappeared from Prometheus target discovery.

## Impact

The cluster will not be kept up to date and upgrades will not be possible.

## Diagnosis

The operator may be down or disabled. Inspect the openshift-cluster-version namespace for events or changes to the cluster-version-operator deployment or pods to diagnose and repair.

## Mitigation

The resolution depends on the particular issue reported in the logs.
