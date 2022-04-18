**PagerDuty Incident:** https://redhat.pagerduty.com/incidents/Q2U2R731W61200

**Alert:** AAPPodContainerTerminated

**Severity:** critical

**Cluster:** cicd-aap-aas-ansible-c-eastus

**Issue:** https://issues.redhat.com/browse/AAP-2632

**Description:** AAP Pod can not running

**Log:**

```
psycopg2.errors.ReadOnlySqlTransaction: cannot execute UPDATE in a read-only transaction
django.db.utils.InternalError: cannot execute UPDATE in a read-only transaction
```
**Debugging:**

```
$ k get po -n ansible-automation-platform
NAME                                               READY   STATUS             RESTARTS   AGE
automation-controller-6bd4694d45-k7bwx             4/4     Running            0          28d
automation-hub-api-6968b5ccbc-sshqz                1/1     Running            3          56d
automation-hub-content-6b47ccb857-5pwwv            1/1     Running            0          56d
automation-hub-content-6b47ccb857-qt46p            1/1     Running            0          56d
automation-hub-redis-5d9dfcb967-829m9              1/1     Running            0          56d
automation-hub-resource-manager-7df869f85d-ms2c5   1/1     Running            0          56d
automation-hub-web-6b8c8dc77c-n9r7d                1/1     Running            3          56d
automation-hub-worker-645c4799d8-86rrz             0/1     CrashLoopBackOff   7516       56d
automation-hub-worker-645c4799d8-ftnp8             0/1     CrashLoopBackOff   7567       56d

$ k logs automation-hub-worker-645c4799d8-ftnp8
+ /usr/bin/wait_on_postgres.py
Waiting on postgresql to start...
Checking postgres host psql-aapaasaapc-eastus.postgres.database.azure.com
Checking postgres port 5432
Postgres started!
+ /usr/bin/wait_on_database_migrations.sh
Checking for database migrations
Database migrated!
++ python3 -c 'import sys; from packaging.version import parse; from pulpcore.app.apps import PulpAppConfig; print('\''yes'\'' if parse(PulpAppConfig.version) >= parse('\''3.13.0.dev0'\'') else '\''no'\'')'
+ NEW_TASKING_SYSTEM=yes
+ echo yes
+ [[ yes == \n\o ]]
+ export PATH=/usr/local/bin:/usr/bin/
+ PATH=/usr/local/bin:/usr/bin/
+ pulpcore-worker
yes
pulp [None]: pulpcore.tasking.entrypoint:INFO: Starting distributed type worker
Traceback (most recent call last):
  File "/usr/lib/python3.8/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
psycopg2.errors.ReadOnlySqlTransaction: cannot execute UPDATE in a read-only transaction


The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/usr/bin/pulpcore-worker", line 11, in <module>
    load_entry_point('pulpcore==3.15.2', 'console_scripts', 'pulpcore-worker')()
  File "/usr/lib/python3.8/site-packages/click/core.py", line 829, in __call__
    return self.main(*args, **kwargs)
  File "/usr/lib/python3.8/site-packages/click/core.py", line 782, in main
    rv = self.invoke(ctx)
  File "/usr/lib/python3.8/site-packages/click/core.py", line 1066, in invoke
    return ctx.invoke(self.callback, **ctx.params)
  File "/usr/lib/python3.8/site-packages/click/core.py", line 610, in invoke
    return callback(*args, **kwargs)
  File "/usr/lib/python3.8/site-packages/pulpcore/tasking/entrypoint.py", line 44, in worker
    NewPulpWorker().run_forever()
  File "/usr/lib/python3.8/site-packages/pulpcore/tasking/pulpcore_worker.py", line 59, in __init__
    self.worker = handle_worker_heartbeat(self.name)
  File "/usr/lib/python3.8/site-packages/pulpcore/tasking/worker_watcher.py", line 37, in handle_worker_heartbeat
    worker.save()
  File "/usr/lib/python3.8/site-packages/django_lifecycle/mixins.py", line 134, in save
    save(*args, **kwargs)
  File "/usr/lib/python3.8/site-packages/django/db/models/base.py", line 726, in save
    self.save_base(using=using, force_insert=force_insert,
  File "/usr/lib/python3.8/site-packages/django/db/models/base.py", line 763, in save_base
    updated = self._save_table(
  File "/usr/lib/python3.8/site-packages/django/db/models/base.py", line 845, in _save_table
    updated = self._do_update(base_qs, using, pk_val, values, update_fields,
  File "/usr/lib/python3.8/site-packages/django/db/models/base.py", line 899, in _do_update
    return filtered._update(values) > 0
  File "/usr/lib/python3.8/site-packages/django/db/models/query.py", line 802, in _update
    return query.get_compiler(self.db).execute_sql(CURSOR)
  File "/usr/lib/python3.8/site-packages/django/db/models/sql/compiler.py", line 1559, in execute_sql
    cursor = super().execute_sql(result_type)
  File "/usr/lib/python3.8/site-packages/django/db/models/sql/compiler.py", line 1175, in execute_sql
    cursor.execute(sql, params)
  File "/usr/lib/python3.8/site-packages/django/db/backends/utils.py", line 66, in execute
    return self._execute_with_wrappers(sql, params, many=False, executor=self._execute)
  File "/usr/lib/python3.8/site-packages/django/db/backends/utils.py", line 75, in _execute_with_wrappers
    return executor(sql, params, many, context)
  File "/usr/lib/python3.8/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
  File "/usr/lib/python3.8/site-packages/django/db/utils.py", line 90, in __exit__
    raise dj_exc_value.with_traceback(traceback) from exc_value
  File "/usr/lib/python3.8/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
django.db.utils.InternalError: cannot execute UPDATE in a read-only transaction
```

**Initial Conclusion:**

```
Database is full, so write is blocked.
```

**Resolution:**

- Step 1: Identify issue is due to disk space
Navigate to the Postgres database then click the monitoring tab and check the storage(should be near 100%)
- Step 2: Navigate to the UI and raise the storage(can only be doubled)

**Expected Resolution Time:**  15 minutes unless MSFT Azure has issues

