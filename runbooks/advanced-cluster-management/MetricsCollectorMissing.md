# MetricsCollectorMissing

## Meaning

Metrics collector Pod missing on some managed clusters for longer than 5 minutes.

## Impact

We will miss the metrics from the managed cluster side.

## Diagnosis

To check the ObservabilityAddon status on managed cluster side, make sure the ObservabilityAddon status is ready.

```
$ kubectl get oba observability-addon -o yaml
apiVersion: observability.open-cluster-management.io/v1beta1
kind: ObservabilityAddon
metadata:
  creationTimestamp: "2022-05-17T00:09:38Z"
  generation: 1
  name: observability-addon
  namespace: open-cluster-management-addon-observability
  ownerReferences:
  - apiVersion: work.open-cluster-management.io/v1
    kind: AppliedManifestWork
    name: df930bc2f6e4f150e2ef639212e16e7002abf9ca101e836a975b365d977691a3-cluster1-observability
    uid: 665d434a-3b69-4c2b-ad8a-b96569210ce1
  resourceVersion: "15021782"
  uid: 3e8ba093-74e9-4c59-86d8-22c832e9fe4a
spec:
  enableMetrics: true
  interval: 30
  resources:
    limits:
      cpu: 200m
      memory: 700Mi
    requests:
      cpu: 10m
      memory: 100Mi
status:
  conditions:
  - lastTransitionTime: "2022-05-17T00:09:48Z"
    message: Metrics collector deployed
    reason: Deployed
    status: "False"
    type: Progressing
  - lastTransitionTime: "2022-05-17T00:09:53Z"
    message: Cluster metrics sent successfully
    reason: Available
    status: "True"
    type: Available
```

The `oba.spec.enableMetrics` should be `true`, and the status should contain this message: `Cluster metrics sent successfully`.

And then to check the metrics collector pod logs on managed cluster side, the pod should have the following log:

```
$ kubectl logs metrics-collector-deployment-85cc68c6f7-jtgbm
...
level=info caller=logger.go:45 ts=2022-05-17T06:14:54.557817478Z component=forwarder component=metricsclient msg="Metrics pushed successfully"
level=debug caller=logger.go:40 ts=2022-05-17T06:15:26.849664654Z component=forwarder component=metricsclient timeseriesnumber=11945
level=info caller=logger.go:45 ts=2022-05-17T06:15:26.970931464Z component=forwarder component=metricsclient msg="Metrics pushed successfully"
level=debug caller=logger.go:40 ts=2022-05-17T06:15:59.049874905Z component=forwarder component=metricsclient timeseriesnumber=11945
level=info caller=logger.go:45 ts=2022-05-17T06:15:59.343574523Z component=forwarder component=metricsclient msg="Metrics pushed successfully"
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
