# Update OSD Addons

## Meaning

This runbook will help guide through how to add or update an OSD addon provided we have the bundle in an image format.

## Impact

Updating the OSD addons is a quick process, but it can take about 30 minutes - 1 hour to see changes in the staging or integration environments after code is merged.

## Steps

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
