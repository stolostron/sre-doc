# ArgoCDSyncAlert

## Meaning

This alert is triggered when ArgoCD application is out of sync.

## Impact

ArgoCD application actual status is inconsistent with the set status.

## Diagnosis

Check the status of ArgoCD application:

```console
$ oc describe app <argocd-app-name> -n openshift-gitops
```

## Mitigation

The resolution depends on the particular issue reported in the logs.
