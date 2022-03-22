**Alert Name:** AutomationControllerResponseError

**Description:** AAP controller in ansible-automation-platform namespace response error (status="500") is more than 3 over 5 minutes. 

**Severity:** warning

**Service:** Ansible Automation Platform

**Dependencies:** n/a

**Troubleshooting:** To check the AAP automation-controller-web container, we can found some error log (status="500")

**Related Alerts:** n/a

**Root Cause:**
1. AAP controller web server has an intenal error. We will found the following error log from automation-controller-web container:
```
10.244.0.142 - admin [24/Jan/2022:13:49:58 +0000] "GET /api/v2/metrics HTTP/1.1" 500 0 "-" "Prometheus/2.26.1" "-"
```

**Resolution:**
- Root Cause 1
    - Step 1: Check the automation-controller-web server to make sure the metrics endpoint works well

**Dashboards:** n/a

**Related Links:** n/a
