# How-to guides

## How to enable DHCP on an interface

To let the interface named `enp3s0` get an address via DHCP, create a YAML file with the
following:

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: true
```

## How to configurate a static IP address on an interface

To set a static IP address, use the `addresses` keyword, which takes a list of IPv4 or
IPv6 addresses along with the subnet prefix length (e.g. /24).

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses:
        - 10.10.10.2/24
```