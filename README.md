# Linux Networking Lab  host-only + NAT 

## Overview 
This project documents the design and troubleshooting of a dual-interface Linux lab enviroment built in a hypervisor.

The lab includes:
- One client machine
- One server machine
- internal isolated network 
- External connectivity via NAT
 

## Objectives 
- Understand Linux routing fundamentals
- Differentiate routing vs DNS issue
- configure static IP and DHCP interfaces
- Debug connectivity using first-principles

## Lab Desing 

### Internal Network
- Subnet: 192.168.x.0/24
- Static IP addressing
- No default gateway 

### NAT Network 
- DHCP
- Provides default route for Internet Access

## Key Learning Points 
- 'ip route' is the primary diagnostic command
- DNS does not work without routing 
- YAML indentation matters in netplan 
- NetworkManager and netplan behave differently
