# PolicyNotCompliant

## Meaning

Policy is not compliant for longer than 5 minutes.

## Impact

We have some violations for the policy in the cluster.

## Diagnosis

To login the ACM console and check the policy status, you can find the reason, for example：

![](/images/PolicyNotCompliant.png)

You can also find the reason from the cli:

```
kubectl get policy $NS.$POLICY_NAME -n $CLUSTER_NAME -o yaml
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
