Field | Required | Default Value | Description
:---: | :---: |  :---: | :---
name | y | n/a | alert name, for example: **InstanceDown**
annotations.summary | y | n/a |
annotations.description | y | n/a |
labels.severity | y | <br> info <br> warning <br> critical |
labels.team | y | n/a | For example: [acm-sre, aap-sre, acm-aap-sre]
labels.cluster | y | n/a |
labels.service | y | n/a | Which service is belong to this alert
label.runbook | y | n/a | For example: https://github.com/stolostron/sre-doc/blob/main/runbook/InstanceDown.md
labels.namespace | n | n/a |
labels.pod | n | n/a |
labels.container  | n | n/a |
labels.dashboard  | n | n/a |

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
