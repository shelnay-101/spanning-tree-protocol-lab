# 02 - Addressing Plan

## Management (VLAN 99, 192.168.99.0/24)

| Device | Interface | IP address |
|---|---|---|
| DSW1 | VLAN 99 | 192.168.99.11 |
| DSW2 | VLAN 99 | 192.168.99.12 |
| ASW1 | VLAN 99 | 192.168.99.21 |
| ASW2 | VLAN 99 | 192.168.99.22 |
| ASW3 | VLAN 99 | 192.168.99.23 |
| ASW4 | VLAN 99 | 192.168.99.24 |

Mask: 255.255.255.0. There is no gateway for VLAN 99 in this lab, so management
is reachable only inside the VLAN.

## User VLAN gateways (HSRP)

| VLAN | Subnet | Virtual gateway | DSW1 SVI | DSW2 SVI |
|---|---|---|---|---|
| 10 | 192.168.10.0/24 | 192.168.10.1 | 192.168.10.2 | 192.168.10.3 |
| 20 | 192.168.20.0/24 | 192.168.20.1 | 192.168.20.2 | 192.168.20.3 |
| 30 | 192.168.30.0/24 | 192.168.30.1 | 192.168.30.2 | 192.168.30.3 |
| 40 | 192.168.40.0/24 | 192.168.40.1 | 192.168.40.2 | 192.168.40.3 |

## End devices

| PC | Switch port | VLAN | IP address | Mask | Gateway |
|---|---|---|---|---|---|
| PC-IT | ASW1 Fa0/10 | 10 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC-SALES | ASW2 Fa0/10 | 20 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |
| PC-FINANCE | ASW3 Fa0/10 | 30 | 192.168.30.10 | 255.255.255.0 | 192.168.30.1 |
| PC-HR | ASW4 Fa0/10 | 40 | 192.168.40.10 | 255.255.255.0 | 192.168.40.1 |
