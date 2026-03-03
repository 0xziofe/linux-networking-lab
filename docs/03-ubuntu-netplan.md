# Ubuntu Server – Netplan Configuration

## Goal
Maintain static lab IP and enable NAT interface via DHCP.

## Configuration Example

```yaml
network:
  version: 2
  ethernets:
    lab_interface:
      dhcp4: no
      addresses:
        - 192.168.X.10/24
    nat_interface:
      dhcp4: yes


## Apply 

sudo netplan apply


## Common Error
Invalid YAML:inconsistent indentation

Cause:
YAML requires strict spacing.


## Verification
ip -br a
ip route

Expected: 
Presence of default route via NAT interface.
