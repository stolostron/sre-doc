# AAPEndpointAddressNotReady

## Meaning

AAP endpoint address is not ready.

## Impact

AAP endpoint address is not ready which means some AAP Pods are not ready.

## Diagnosis

To check the endpoint name from the alert description, and then to check the AAP Pod status, the Pod status is not `Running`, it should be `Pending` or `Unknown` or `Failed`, and check the AAP pod log if we can find some reason.

## Mitigation

The resolution depends on the particular issue reported in the logs.
