# KubeControllerManagerDown

## Meaning

This alert is triggered when KubeControllerManager has disappeared from Prometheus target discovery.

## Impact

The cluster will not be kept up to date and upgrades will not be possible.

## Diagnosis

The KubeControllerManager may be down or disabled. Inspect the kube-system namespace for events or changes to diagnose and repair.

## Mitigation

The resolution depends on the particular issue reported in the logs.
