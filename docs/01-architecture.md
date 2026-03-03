# 01 – Lab Architecture

## Overview

This lab environment was designed to simulate a realistic Linux support scenario involving:

- Internal VM-to-VM communication
- External Internet connectivity
- Separation between lab traffic and outbound traffic
- Static and dynamic interface configuration

The setup uses a dual-interface model to maintain clarity between internal networking and external access.

---

## Virtual Machines

### LAB_CLIENT
- OS: Kali Linux
- Role: Client / troubleshooting workstation

### LAB_SERVER
- OS: Ubuntu Server (minimal)
- Role: Service-oriented server environment

---

## Network Design

### 1) Internal Network (Host-only)

Purpose:
- Allow communication between lab machines only
- Simulate an isolated internal LAN

Configuration:
- Subnet: `192.168.X.0/24`
- Static addressing
- No default gateway defined

This network is used for:
- Inter-VM communication
- Controlled troubleshooting scenarios

---

### 2) External Network (NAT)

Purpose:
- Provide Internet connectivity
- Allow package updates and dependency installation

Configuration:
- DHCP enabled
- Default route provided automatically by hypervisor

This network is used only for:
- Outbound Internet traffic
- System updates
- Tool installation

---

## Interface Strategy

Each VM uses two interfaces:

| Interface Type | Purpose | IP Mode |
|---------------|----------|---------|
| Host-only     | Internal lab traffic | Static |
| NAT           | Internet access | DHCP |

This separation prevents:

- Mixing lab traffic with external routing
- Accidental dependency on Internet for internal tests
- Routing ambiguity

---

## Design Rationale

The dual-interface model was chosen to:

- Preserve deterministic lab behavior
- Allow structured troubleshooting
- Practice routing table analysis
- Understand dependency between routing and DNS

The routing table (`ip route`) is considered the primary source of truth in this architecture.
