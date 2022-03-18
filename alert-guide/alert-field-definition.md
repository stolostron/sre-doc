Field | Required | Default Value | Description
:---: | :---: |  :---: | :---
name | y | n/a | [valid alert name](https://prometheus.io/docs/concepts/data_model/#metric-names-and-labels), for example: **InstanceDown**
annotations.summary | y | n/a | alert summary
annotations.description | y | n/a | alert description
labels.severity | y |<br> info <br> warning <br> critical |<br> info: alerts as records, it is a low erverity  <br> warning: alerts as notification, it is a warning erverity  <br> critical: the urgent alert, need on-call SRE to handle it
labels.team | y | n/a | for example: [acm-sre, aap-sre, acm-aap-sre]
labels.cluster | y | n/a | which cluster firing this alert
labels.service | y | n/a | which service is belong to this alert
label.runbook | y | n/a | for example: https://github.com/stolostron/sre-doc/blob/main/runbook/InstanceDown.md
labels.namespace | n | n/a | which namespace is the service belongs to
labels.pod | n | n/a | which pod is the service belongs to
labels.container  | n | n/a | which container is the service running on
labels.dashboard  | n | n/a | the alert related dashboard link

Following this template to define an alert:

```yaml
- alert: InstanceDown
  annotations:
    summary: "Instance {{ $labels.instance }} down"
    description: "{{ $labels.instance }} of job {{ $labels.job }} has been down for more than 5 minutes."
  expr: up == 0
  for: 5m
  labels:
    severity: critical
    team: acm-sre
    cluster: cluster1
    service: service1
    runbook: https://github.com/stolostron/sre-doc/blob/main/runbook/InstanceDown.md
    namespace: ns1
    pod: pod1
    container: c1
    dashboard: https://grafana_dashboard_url/dashboard1
```

## links

- defining alerting rules: https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/
