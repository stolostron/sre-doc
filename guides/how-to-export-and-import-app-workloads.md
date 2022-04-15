## How to export and import the AAP workloads

- Fetch the AAP controller admin password:

```
$ oc get secret automation-controller-admin-password -n ansible-automation-platform -o json | jq -r '.data.password' | base64 -d
```

- Make sure you can login the AAP:

```
$ awx login --conf.host https://app-controller.com/ --conf.username $USERNAME --conf.password $PASSWORD
```

- Export the workloads from AAP:

```
$ awx export --conf.host https://app-controller.com/ --conf.username $USERNAME --conf.password $PASSWORD > resource.json
```

- Import the workloads to another AAP:

```
$ awx import < resource.json --conf.host https://app-controller.com/ --conf.username $USERNAME --conf.password $PASSWORD
```

## Links

- https://docs.ansible.com/ansible-tower/latest/html/towercli/examples.html#import-export
- https://docs.ansible.com/ansible-tower/latest/html/towercli/usage.html#installation
