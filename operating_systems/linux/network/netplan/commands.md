# Netplan commands

## netplan

```shell
netplan
```

Type this command to see available sub-commands.

## Showing current Netplan configuration

```shell
netplan get
```

By default, you should see an output similar to the one below:

```yaml
network:
  version: 2
  ethernets:
    enp1s0:
      dhcp4: true
```

This means:

- There's an Ethernet interface called `enp1s0`
- DHCP is enabled for the IPv4 protocon on `enp1s0`

## Showing current network configuration

```shell
netplan status --all
```

You should see an output similar to the one below:

```
     Online state: online
    DNS Addresses: 127.0.0.53 (stub)
       DNS Search: .

●  1: lo ethernet UNKNOWN/UP (unmanaged)
      MAC Address: 00:00:00:00:00:00
        Addresses: 127.0.0.1/8
                   ::1/128
           Routes: ::1 metric 256

●  2: enp1s0 ethernet UP (networkd: enp1s0)
      MAC Address: 52:54:00:96:06:18 (Red Hat, Inc.)
        Addresses: 192.168.122.101/24 (dhcp)
                   fe80::5054:ff:fe96:618/64 (link)
    DNS Addresses: 192.168.122.1
           Routes: default via 192.168.122.1 from 192.168.122.101 metric 100 (dhcp)
                   192.168.122.0/24 from 192.168.122.101 metric 100 (link)
                   192.168.122.1 from 192.168.122.101 metric 100 (dhcp, link)
                   fe80::/64 metric 256
```
