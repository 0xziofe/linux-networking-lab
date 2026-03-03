# Kali - Routing Troubleshooting 

## Sympton 
Internet connectivity failed: 
- 'ping 8.8.8.8' -> Network Unreachable 

## Diagnostic Steps

- ip -br a
- ip route
- cat /etc/resolv.conf
- nmcli connection show

## Root Cause

The NAT interface was configured with: 
- ipv4.method:manual
- no gateway defined 
causing a default route to appear missing

## Fix

nmcli connection modify "<connection-name>" ipv4.method auto
nmcli connection down "<connection-name>"
nmcli connection up "<connection-name>"

## Verification
ip route -> you should see a default route gateway
ping 8.8.8.8 -> work



## Techincal Insight 
DNS configuration alone does not enable connectivity, a default route must exist.
