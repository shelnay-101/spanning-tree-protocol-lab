# 01 - Design Overview

## Goal

Simulate a two-tier enterprise campus network (distribution + access) that demonstrates:

1. Rapid-PVST+ with per-VLAN root bridges (load balancing)
2. EtherChannel (LACP) between the two distribution switches
3. DTP disabled on all ports
4. VTP v2 with a single server
5. HSRP v2 first-hop redundancy aligned with the STP roots

## Tiers

| Tier | Switches | Role |
|---|---|---|
| Distribution | DSW1, DSW2 | STP roots, HSRP gateways, inter-VLAN routing (SVIs), VTP server (DSW1). |
| Access | ASW1-ASW4 | End-device ports, dual-homed to DSW1 and DSW2. |

There is no core switch. The dual-homed access switches and the DSW1-DSW2 EtherChannel
already create the loops that Spanning Tree has to block.

## VLANs

| VLAN | Name | Subnet | Purpose |
|---|---|---|---|
| 10 | IT | 192.168.10.0/24 | PC-IT |
| 20 | SALES | 192.168.20.0/24 | PC-SALES |
| 30 | FINANCE | 192.168.30.0/24 | PC-FINANCE |
| 40 | HR | 192.168.40.0/24 | PC-HR |
| 99 | MGMT | 192.168.99.0/24 | Management SVIs, also trunk native VLAN |
| 999 | BLACKHOLE | none | Unused ports parked here and shut down |

## VTP

| Setting | Value |
|---|---|
| Domain | `ENTERPRISE` |
| Version | 2 |
| Password | `Cisco123` (lab only) |
| Server | DSW1 |
| Clients | DSW2, ASW1-ASW4 |

VLANs are created on DSW1 only. Clients cannot create, rename or delete VLANs.
If DSW1 fails, clients keep their VLANs but no VLAN changes are possible until a
server returns. For redundancy, DSW2 can also be set to server mode with the same
domain and password.

## Spanning Tree (Rapid-PVST+)

| Switch | VLAN 10, 20 | VLAN 30, 40 | VLAN 1, 99 |
|---|---|---|---|
| DSW1 | 4096 (root) | 8192 (backup) | 8192 |
| DSW2 | 8192 (backup) | 4096 (root) | 8192 |
| ASW1-4 | default 32768 + VLAN ID | default | default |

Result: each access switch forwards VLAN 10 and 20 traffic toward DSW1, and
VLAN 30 and 40 toward DSW2. The other uplink is Alternate (discarding) per VLAN.

## EtherChannel

- DSW1 Fa0/23-24 and DSW2 Fa0/23-24 form `Port-channel 1`
- Protocol: LACP, both ends `active`
- Port-channel carries VLANs 10, 20, 30, 40, 99 with native VLAN 99

## DTP

DTP is disabled with `switchport nonegotiate` on every trunk. Edge ports use
`switchport mode access`. Unused ports (including Fa0/1 on the DSWs) are access ports
in VLAN 999 and shut down.

## HSRP

| VLAN | Virtual IP | DSW1 | DSW2 | Active |
|---|---|---|---|---|
| 10 | 192.168.10.1 | .2 (prio 110) | .3 (prio 100) | DSW1 |
| 20 | 192.168.20.1 | .2 (prio 110) | .3 (prio 100) | DSW1 |
| 30 | 192.168.30.1 | .2 (prio 100) | .3 (prio 110) | DSW2 |
| 40 | 192.168.40.1 | .2 (prio 100) | .3 (prio 110) | DSW2 |

The active HSRP router for each VLAN is also the STP root for that VLAN, so
traffic takes the shortest path to its gateway.

## Edge protection

- `spanning-tree portfast default` and `bpduguard default` on access switches
- Per-port `portfast` and `bpduguard enable` on PC ports (Fa0/10)
