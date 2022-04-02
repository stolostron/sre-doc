# PrometheusErrorSendingAlertsToSomeAlertmanagers

## Meaning

This alert is triggered when Prometheus has encountered more than 1% errors sending alerts to a specific Alertmanager.

## Impact

Alerts may be missing or inaccurate.

## Diagnosis

Note if Prometheus cannot send alerts it's likely AlertManager is failing.

## Mitigation

The resolution depends on the particular issue reported in the logs.
