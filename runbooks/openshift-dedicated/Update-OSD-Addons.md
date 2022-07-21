# Update OSD Addons

## Meaning

This runbook will help guide through how to add or update an OSD addon provided we have the bundle in an image format.

## Impact

The updating of OSD addons is quick if automatic and mostly consists of approving merge requests.

If run manual it can take about 30 minutes to update the addons.

Once the merge requests have been merged, it can take 30 minutes to 1 hour to see changes in the staging or integration environments after code is merged.

# Method - Automation

A GitHub Action - [update-osd-addon-config](https://github.com/stolostron/openshift-pipelines/actions/workflows/update-osd-addon-config.yml) runs once per day to check if there are any updates to the downstream bundle images. If an update does exist, the GitHub action will create a pull-request with the update to the config.yaml. This GitHub action can be triggered automatically as well.

If a pull request has been created by the GitHub action it should be merged. Next, we can trigger the OpenShift Pipelines task to create a GitLab merge request.

This OpenShift Pipelines task will need to run on a cluster behind the Red Hat VPN.

The [submit-osd-addon-update](https://github.com/stolostron/openshift-pipelines/blob/main/addon-bundling/pipeline/pipeline.yaml) pipeline can be triggered. This pipeline reads the [config.yaml](https://github.com/stolostron/openshift-pipelines/blob/main/addon-bundling/config.yaml) and if an update exists, it will create a GitLab merge request to [managed-tenants-bundles](https://gitlab.cee.redhat.com/service/managed-tenants-bundles).

From here, we can add an `/lgtm` to the merge request. It should merge automatically once the pipeline completes.

Once merged, another merge request will be create in the [managed-tenants](https://gitlab.cee.redhat.com/service/managed-tenants) repository. We can add an `/lgtm` to this merge request as well. It should merge automatically once the pipeline completes.

For issues diagnosing pipeline failures, first check the logs of the pipeline. If it is an irregular error, ping #service-development or #service-development-b slack channels.


## Deploying Automation on a fresh cluster

Ensure the cluster you would like to deploy the OpenShift Pipeline too is behind the Red Hat VPN.

Next complete the following - 
1. Install the OpenShift Pipelines operator on the cluster.
2. Create the namespace `osd-addon-bundling`
3. Fill in and apply the [prereqs](https://github.com/stolostron/openshift-pipelines/blob/main/addon-bundling/pipeline/prereqs/secrets_template.yaml) secret
4. Apply the following [manifests](https://github.com/stolostron/openshift-pipelines/tree/main/addon-bundling/pipeline)
    1. The manifests contain a [Trigger](https://github.com/stolostron/openshift-pipelines/blob/main/addon-bundling/pipeline/trigger.yaml), to ensure that the Pipeline can fire based on a CronJob.
5. Run the Pipeline

## Method - Manual

1. Clone the following [repository](https://github.com/stolostron/openshift-pipelines).
    1. If this is your first time forking the repo, you will need to add the App SRE bot (@devtools-bot) as a Maintainer in your code repo. Otherwise the Pipeline build will fail at a later step.
2. Enter the addon-bundling directory - `cd addon-bundling/`
3. Ensure the contents of [config.yaml](https://github.com/stolostron/openshift-pipelines/blob/main/addon-bundling/config.yaml) is correct. Addons can be updated, added or removed directly to generate their corresponding OSD Addons. For help with the format of this file, see the following [README](https://github.com/stolostron/openshift-pipelines/tree/main/addon-bundling#format)
4. Once the config file is finalized, run - `make bundles` to generate the bundles
5. The [managed-tenants-bundles](https://gitlab.cee.redhat.com/service/managed-tenants-bundles) repository must be forked
6. Copy over the contents of the generated bundles/* directory to the addons/* directory. See sample command below - 
```bash
$ cp -r bundles/* ~/path/to/managed-tenants-bundles/addons
```
7. Submit merge request to the managed-tenants-bundles repository. We should also be able to approve these merge requests, provided that our gitlab IDs are present [here](https://gitlab.cee.redhat.com/service/managed-tenants-bundles/-/blob/main/addons/advanced-cluster-management/OWNERS). If onboarding or updating another bundle, ensure your OWNERS file is correct or message #forum-managed-tenants for approval.
8. Once merge request has been submitted, ensure that the associated Pipeline build passes. If it does not, this will need to be corrected before proceeding. Check the logs of the Pipeline for more details. If it passes, an OWNER can /lgtm.
    1. Ensure the managed-tenants App SRE bot (@devtools-bot) as a Maintainer in your code repo.
9. After the MR to managed-tenants-bundles has been merged, a Pipeline will trigger another build, which will automatically generate a new MR to the [managed-tenants](https://gitlab.cee.redhat.com/service/managed-tenants) repo.
10. If you are an OWNER, approve the generated MR to [managed-tentants](https://gitlab.cee.redhat.com/service/managed-tenants) repository to update the addons once the builds have passed. If the builds fail, see logs for more details.
11. Once the MR to [managed-tenants](https://gitlab.cee.redhat.com/service/managed-tenants) repository has been merged, it can take up to 30 minutes before these changes are visible in Staging or Integration environments.
