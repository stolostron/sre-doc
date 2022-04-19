# PolicyNotCompliant

## Meaning

The policy is not compliant for longer than 5 minutes.

## Impact

We have some violations of the policy in the cluster.

## Diagnosis

To login to the ACM console and check the policy status, you can find the reason, for example：

![](/images/PolicyNotCompliant.png)

You can also find the reason from the command line:

```
kubectl get policy $NS.$POLICY_NAME -n $CLUSTER_NAME -o yaml
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
