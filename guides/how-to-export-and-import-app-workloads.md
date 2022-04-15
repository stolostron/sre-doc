## how to export and import the AAP workloads

- Export the workloads from AAP:

```
$ awx export --conf.host https://app-controller.com/ --conf.username $USERNAME --conf.password $PASSWORD > workloads.json
```

- Import the workloads to AAP:

```
$ awx import < workloads.json --conf.host https://app-controller.com/ --conf.username $USERNAME --conf.password $PASSWORD
```

## Links

- https://docs.ansible.com/ansible-tower/latest/html/towercli/examples.html#import-export
- https://docs.ansible.com/ansible-tower/latest/html/towercli/usage.html#installation
