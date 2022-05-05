# Problem

We adding and removing managed clusters from the ACM hub, in some cases, the grafana dashboard will *NOT* display all the metrics data for all clusters that have observability enabled and metrics being collected.

When you parse the metrics collector logs on the managed cluster side, it shows metrics successfully push to observability.

The root cause seems to be your grafana session is cache the list of cluster it is aware off based on your user id.

If you keep your grafana browser opened, and continue to add / remove managed clusters.

The browser cache and what's in the ACM system becomes out of sync.

# Workaround

Force restart of the rbac pod in observability.

```bash
oc get pods observability-rbac-query-proxy-5484fff8df-7wxfh --show-labels
oc delete pod -l app=rbac-query-proxy -n open-cluster-management-observability
```

This will force rbac to reload the list of current managed clusters.

```
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.033984       1 util.go:129] added a managedcluster: xian
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034007       1 util.go:129] added a managedcluster: boston
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034013       1 util.go:129] added a managedcluster: canada
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034017       1 util.go:129] added a managedcluster: local-cluster
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034022       1 util.go:129] added a managedcluster: belgium
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034027       1 util.go:129] added a managedcluster: singapore
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034040       1 util.go:129] added a managedcluster: hong-kong
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034044       1 util.go:129] added a managedcluster: ireland
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034051       1 util.go:129] added a managedcluster: toronto
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034063       1 util.go:129] added a managedcluster: obs-build
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034068       1 util.go:129] added a managedcluster: albania
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034072       1 util.go:129] added a managedcluster: brazil
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034077       1 util.go:129] added a managedcluster: spain
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034085       1 util.go:129] added a managedcluster: australia
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034092       1 util.go:129] added a managedcluster: frankfurt
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034097       1 util.go:129] added a managedcluster: obs-scale
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034103       1 util.go:129] added a managedcluster: shanghai
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:08.034108       1 util.go:129] added a managedcluster: austin
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:34.296580       1 util.go:70] user <cdoan1> have access to all clusters
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:34.311406       1 util.go:70] user <cdoan1> have access to all clusters
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:34.437245       1 util.go:70] user <cdoan1> have access to all clusters
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:34.438941       1 util.go:70] user <cdoan1> have access to all clusters
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:34.439409       1 util.go:70] user <cdoan1> have access to all clusters
observability-rbac-query-proxy-5484fff8df-6hq4w rbac-query-proxyobservability-rbac-query-proxy-5484fff8df-cxvc4  I0504 23:55:34.606779       1 util.go:70] user <cdoan1> have access to all clusters
rbac-query-proxy I0504 23:55:34.584131       1 util.go:70] user <cdoan1> have access to all clusters
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:34.600915       1 util.go:70] user <cdoan1> have access to all clusters
observability-rbac-query-proxy-5484fff8df-cxvc4 rbac-query-proxy I0504 23:55:34.620149       1 util.go:70] user <cdoan1> have access to all clusters
observability-rbac-query-proxy-5484fff8df-6hq4w rbac-query-proxy I0504 23:55:34.757096       1 util.go:70] user <cdoan1> have access to all clusters
```
