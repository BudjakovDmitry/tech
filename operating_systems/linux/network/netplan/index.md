# Netplan

- [Netplan configuration]()
- [Netplan commands](commands.md)
- [How-to guides](howto.md)

Netplan is a utility for easily configuring network on a Linux system. You create a
description of the required interfaces and define what each should do.

Netplan reads network configuration from `/etc/netplan/*.yaml` which are written by
administrators, installers, cloud image instantiations, or other OS deployments. During
early boot, Netplan generates backend specific configuration files in `/run` to hand off
control of devices to particular networking daemon.

Netplan currently works with these supported renderers:

- NetworkManager
- Systemd-network

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
