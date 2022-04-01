# KubeStateMetricsWatchErrors

## Meaning

kube-state-metrics is experiencing errors in watch operations.

## Impact

kube-state-metrics is experiencing errors at an elevated rate in watch operations. This is likely causing it to not be able to expose metrics about Kubernetes objects correctly or at all.

## Diagnosis

Check the status of kube-state-metrics pods:

```console
$ oc logs <kube-state-metrics-pod-name> -n openshift-monitoring
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
