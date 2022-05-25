# ManagedClusterMissing

## Meaning

Managedcluster missing from ACM Hub for longer than 10 minutes.

## Impact

Managedclusters have been down or missing, we lost some managed clusters from the ACM Hub side.

## Diagnosis

To check all managedcluster status on the ACM Hub side, make sure all managedcluster status is ready and available:

```
$ kubectl get managedcluster
NAME            HUB ACCEPTED   MANAGED CLUSTER URLS                                            JOINED   AVAILABLE   AGE
demo-cluster    true           https://api.demo-aws-495-s6w87.demo.red-chesterfield.com:6443   True     Unknown     56m
local-cluster   true           https://api.demo-aws-495-7spz8.demo.red-chesterfield.com:6443   True     True        35d
soli-aks-test   true                                                                           True     True        5d1h
```

To login to the ACM console and check all managedclusters status, for example：

![](/images/managedcluster-status.png)

## Mitigation

The resolution depends on the particular issue reported in the logs.
