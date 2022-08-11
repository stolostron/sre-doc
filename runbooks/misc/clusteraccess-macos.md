# Cluster Access

## Meaning

Allow `sshuttle` connection to a private network while using VPN client is connected to a separate VPN.

## Impact

`sshuttle` works fine when there is no VPN client running.

When the VPN client is running, and you launch `sshuttle`, the connection won't work, as there are known issues on **MACOS** when there are 2 VPN. In order to allow the usage of `sshuttle` with this configuration, there are 2 changes needed:

1. Duplicate and Update the VPN Client Profile (Viscosity) and set the `DNS Settings: Mode:` to `Split DNS`

    > NOTE: domains should already be set in your profile

2. Change how we run `sshuttle` command. You can run this script here: https://github.com/andreadecorte/sre-scripts/blob/main/cluster-access

```bash
./cluster-access -d <bastionIP>
```

## Diagnosis


## Mitigation

