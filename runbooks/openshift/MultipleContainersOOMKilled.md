# MultipleContainersOOMKilled

## Meaning

This alert is triggered when containers are being killed due to OOM.

## Impact

Multiple containers were out of memory killed within the past 15 minutes. There are many potential causes of OOM errors, however issues on a specific node or containers breaching their limits is common.

## Diagnosis

You’ll need to size the container workload for different node configurations when using memory limits.

## Mitigation

The resolution depends on the particular issue reported in the logs.
