# KubeNodeNotReady

## Meaning

This alert is triggered when a node in a Kubernetes Cluster is in NotReady status.

## Impact

All the workloads that can be evacuated will be rescheduled to other nodes, pending capacity and zonal considerations.

## Diagnosis

Check the status of the Kubernetes nodes:

```console
$ oc get nodes
```

You will see something like
```
acm5-jfm8t-worker-eastus1-jpn5x   NotReady   worker   30d   v1.23.5+3afdacb
```

## Mitigation

You can first try to describe the node if there is some condition that could explain the issue.

Then you can try to fix it with
```
oc debug node/acm5-jfm8t-worker-eastus1-jpn5x
```

Normally this needs a pod to be scheduled on the node itself, which may not work.

You can then try to ssh to the node from the bastion, user is *core*, private key is the one used to deploy the cluster.

If the node is unreachable, you need to try to check from the IaaS side, in case of Azure you can check the Serial Console logs if available. The last way is to restart, below how you can do it from Azure UI.

![](/images/restart-azure.png)
