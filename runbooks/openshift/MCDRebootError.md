# MCDRebootError

## Meaning

This alert is triggered when reboot failed on node, update may be blocked

## Impact

Node can not reboot.

## Diagnosis

Check the status of machine config operator pods:

```console
$ oc logs <machine-config-operator-pod-name> -n openshift-machine-config-operator
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
