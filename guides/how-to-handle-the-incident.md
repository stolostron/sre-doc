# How to handle the incident

This documentation covers the PagerDuty incident response process. When the SRE receives an incident call from PagerDuty, we can follow these steps to handle this incident.

## 1) Follow the runbook to resolve the incident

You can find all runbooks from [doc repo](https://github.com/stolostron/sre-doc). When you receive an incident from PagerDuty, you can search the runbook and follow the steps to resolve the incident. If the runbook does not include the steps to resolve this incident, please create a PR to update the runbook when you resolved the incident. If you can not find any runbook for this incident, please follow the runbook template to create a runbook for this incident.

## 2) Create the issue to trace the incident

You should create an issue on Jira to trace the incident.

## 3) Write an incident report

You should write an incident report and add the report to the issue. Please follow [this report template](./incident-report-template.md) to create it.
