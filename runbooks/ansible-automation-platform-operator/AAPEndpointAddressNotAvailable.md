# AAPEndpointAddressNotAvailable

## Meaning

AAP endpoint address is not available.

## Impact

AAP endpoint address is not available which means there is no ready AAP Pods.

## Diagnosis

To check the endpoint name from the alert description, and then check the AAP Pod status, the Pod status is not `Running`, it should be `Pending` or `Unknown` or `Failed`, and check the AAP pod log if we can find some reason.

## Mitigation

The resolution depends on the particular issue reported in the logs.
