# MachineAPIOperatorMetricsCollectionFailing

## Meaning

This alert is triggered when machine api operator metrics collection is failing.

## Impact

machine api operator metrics may be missing or inaccurate.

## Diagnosis

Check the status of machine api operator pods:

```console
$ oc logs <machine-api-operator-pod-name> -n openshift-machine-api
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
