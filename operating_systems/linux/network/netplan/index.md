# Netplan

- [Netplan configuration](configuration.md)
- [Netplan commands](commands.md)
- [How-to guides](howto.md)

![netplan design overview](/operating_systems/linux/images/netplan_design_overview.svg)

## Commands

```shell
netplan generate
```

Use `/etc/netplan` to generate the required configuration for the renderers.

```shell
netplan apply
```

Apply all configurations for the renderers, restarting them as necessary.

```shell
netplan try
```

Apply configuration and wait for user confirmation; will roll back if network is broken
or no confirmation is given.
