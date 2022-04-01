# Watchdog

## Meaning

This alert that should always be firing to certify that Alertmanager is working properly.

## Impact

The entire alerting pipeline is not functional.

## Diagnosis

Determine whether the Alertmanager is down. This alert is always firing, therefore it should always be firing in Alertmanager and always fire against a receiver.

## Mitigation

The resolution depends on the particular issue reported in the logs.
