# SRE Doc

## [Alert Guide](./alert-guide)

Alert related guide.

- [Alert Template](./alert-guide/alert-field-definition.md) - Follow this template to define a new alert

## [Runbooks](./runbooks/)

- [OpenShift Runbooks](https://github.com/openshift/runbooks)
- [OpenShift Online Runbooks](https://github.com/openshift/ops-sop/tree/master/v4/alerts)
- [Prometheus Operator Ecosystem Runbooks](https://github.com/prometheus-operator/runbooks/tree/main/content/runbooks)

### Ansible Automation Platform

To add a new runbook for Ansible Automation Platform alert, please follow [Ansible Automation Platform runbook template](./runbooks/ansible-automation-platform-operator/runbook-template.md) to create it.

- [AAPDeploymentReplicasMismatch](./runbooks/ansible-automation-platform-operator/AAPDeploymentReplicasMismatch.md)
- [AAPPodContainerTerminated](./runbooks/ansible-automation-platform-operator/AAPPodContainerTerminated.md)
- [AAPPodFrequentlyRestarting](./runbooks/ansible-automation-platform-operator/AAPPodFrequentlyRestarting.md)
- [AAPPodNotReady](./runbooks/ansible-automation-platform-operator/AAPPodNotReady.md)
- [AAPPodRestartingTooMuch](./runbooks/ansible-automation-platform-operator/AAPPodRestartingTooMuch.md)
- [AAPStatefulSetReplicasMismatch](./runbooks/ansible-automation-platform-operator/AAPStatefulSetReplicasMismatch.md)

### OpenShift

To add a new runbook for OpenShift alert, please follow [OpenShift runbook template](https://github.com/openshift/runbooks/blob/master/example.md) to create it.

- [AlertmanagerClusterFailedToSendAlerts](https://github.com/openshift/ops-sop/blob/master/v4/alerts/AlertmanagerClusterFailedToSendAlerts.md)
- [AlertmanagerFailedReload](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/AlertmanagerFailedReload.md)
- [AlertmanagerFailedToSendAlerts](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/AlertmanagerFailedToSendAlerts.md)
- [ArgoCDSyncAlert](./runbooks/openshift/ArgoCDSyncAlert.md)
- [ClusterOperatorDown](https://github.com/openshift/ops-sop/blob/master/v4/alerts/ClusterOperatorDown.md)
- [ClusterVersionOperatorDown](./runbooks/openshift/ClusterVersionOperatorDown.md)
- [etcdBackendQuotaLowSpace](https://github.com/openshift/runbooks/blob/master/alerts/cluster-etcd-operator/etcdBackendQuotaLowSpace.md)
- [etcdGRPCRequestsSlow](https://github.com/openshift/runbooks/blob/master/alerts/cluster-etcd-operator/etcdGRPCRequestsSlow.md)
- [etcdHighFsyncDurations](https://github.com/openshift/runbooks/blob/master/alerts/cluster-etcd-operator/etcdHighFsyncDurations.md)
- [etcdInsufficientMembers](https://github.com/openshift/runbooks/blob/master/alerts/cluster-etcd-operator/etcdInsufficientMembers.md)
- [etcdMembersDown](https://github.com/openshift/runbooks/blob/master/alerts/cluster-etcd-operator/etcdMembersDown.md)
- [etcdNoLeader](https://github.com/openshift/runbooks/blob/master/alerts/cluster-etcd-operator/etcdNoLeader.md)
- [ExtremelyHighIndividualControlPlaneCPU](https://github.com/openshift/ops-sop/blob/master/v4/alerts/ExtremelyHighIndividualControlPlaneCPU.md)
- [HAProxyDown](https://github.com/openshift/ops-sop/blob/master/v4/alerts/HAProxyDown.md)
- [KubeAPIDown](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/KubeAPIDown.md)
- [KubeAPIErrorBudgetBurn](https://github.com/openshift/ops-sop/blob/master/v4/alerts/KubeAPIErrorBudgetBurn.md)
- [KubeControllerManagerDown](./runbooks/openshift/KubeControllerManagerDown.md)
- [KubeletDown](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/KubeletDown.md)
- [KubePersistentVolumeFillingUp](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/KubePersistentVolumeFillingUp.md)
- [KubeQuotaAlmostFull](./runbooks/openshift/KubeQuotaAlmostFull.md)
- [KubeSchedulerDown](./runbooks/openshift/KubeSchedulerDown.md)
- [KubeStateMetricsListErrors](./runbooks/openshift/KubeStateMetricsListErrors.md)
- [KubeStateMetricsWatchErrors](./runbooks/openshift/KubeStateMetricsWatchErrors.md)
- [MachineAPIOperatorMetricsCollectionFailing](./runbooks/openshift/MachineAPIOperatorMetricsCollectionFailing.md)
- [MCDRebootError](./runbooks/openshift/MCDRebootError.md)
- [MultipleContainersOOMKilled](./runbooks/openshift/MultipleContainersOOMKilled.md)
- [NodeFileDescriptorLimit](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/NodeFileDescriptorLimit.md)
- [NodeFilesystemAlmostOutOfFiles](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/NodeFilesystemAlmostOutOfFiles.md)
- [NodeFilesystemAlmostOutOfSpace](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/NodeFilesystemAlmostOutOfSpace.md)
- [NodeFilesystemFilesFillingUp](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/NodeFilesystemFilesFillingUp.md)
- [NodeFilesystemSpaceFillingUp](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/NodeFilesystemSpaceFillingUp.md)
- [NodeRAIDDegraded](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/NodeRAIDDegraded.md)
- [PodDisruptionBudgetLimit](https://github.com/openshift/ops-sop/blob/master/v4/alerts/PodDisruptionBudgetLimit.md)
- [PrometheusErrorSendingAlertsToSomeAlertmanagers](./runbooks/openshift/PrometheusErrorSendingAlertsToSomeAlertmanagers.md)
- [PrometheusTargetSyncFailure](https://github.com/openshift/runbooks/blob/master/alerts/cluster-monitoring-operator/PrometheusTargetSyncFailure.md)
- [Watchdog](./runbooks/openshift/Watchdog.md)

## [SRE Getting Started Guide](https://docs.google.com/document/d/1xk3xaAD7Un89Pg9qEnhXQhqhGwQmzfjA2Cy5MXfZV8g/edit#heading=h.6t0482971ime)

SRE quickstart, helpful documents and links.
