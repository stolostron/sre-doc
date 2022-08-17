# Cluster Access

## Meaning

Allow `sshuttle` connection to a private network while using VPN client is connected to a separate VPN.

## Impact

`sshuttle` works fine when there is no VPN client running.

When the VPN client is running, and you launch `sshuttle`, the connection won't work, as there are known issues on **MACOS** when there are 2 VPN. In order to allow the usage of `sshuttle` with this configuration, there are some changes needed depending on the DNS setup of your target.

### Public DNS Records

If your DNS records are resolvable publicly, you can skip the DNS resolution through `sshuttle` and just use the following command based on a little sshuttle wrapper coming from https://github.com/andreadecorte/sre-scripts/blob/main/cluster-access

```bash
./cluster-access <bastionIP or Name>
```

### Private DNS records

If your DNS is not public, you need two changes:

1. Duplicate and Update the VPN Client Profile (Viscosity) and set the `DNS Settings: Mode:` to `Split DNS`

    > NOTE: domains should already be set in your profile

2. Run the following command based on a little sshuttle wrapper coming from https://github.com/andreadecorte/sre-scripts/blob/main/cluster-access

```bash
./cluster-access -d <bastionIP or Name>
```

## Diagnosis


## Mitigation

