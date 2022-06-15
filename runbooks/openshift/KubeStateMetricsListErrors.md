# KubeStateMetricsListErrors

## Meaning

This alert is triggered when kube-state-metrics is experiencing errors in list operations. You can check the upstream alert definiton [here](https://github.com/kubernetes/kube-state-metrics/blob/master/examples/prometheus-alerting-rules/alerts.yaml).

## Impact

kube-state-metrics is experiencing errors at an elevated rate in list operations. This is likely causing it to not be able to expose metrics about Kubernetes objects correctly or at all.

## Diagnosis
### Hub
If the issue is reported on the Hub, you should check the status of kube-state-metrics pods:

```console
$ oc logs <kube-state-metrics-pod-name> -n openshift-monitoring
```
### Managed clusters
If the issue is reported on a managed cluster, you should check the status of kube-state-metrics pods there:
```console
$ oc logs <kube-state-metrics-pod-name> -n open-cluster-management-addon-observability
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
