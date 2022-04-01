# KubeSchedulerDown

## Meaning

This alert is triggered when kubeScheduler has disappeared from Prometheus target discovery.

## Impact

This is a critical alert. The kubeScheduler is not responding. The cluster may partially or fully non-functional.

## Diagnosis

Check the status of openshift kube scheduler pods:

```console
$ oc logs <openshift-kube-scheduler-pod-name> -n openshift-kube-scheduler
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
