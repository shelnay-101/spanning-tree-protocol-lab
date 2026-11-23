# Verification Commands

## VTP and VLANs

| Command | Run on | Expected |
|---|---|---|
| `show vtp status` | all | DSW1 Server, others Client; same domain and revision |
| `show vlan brief` | all | VLANs 10, 20, 30, 40, 99, 999 present |

## Trunks and DTP

| Command | Run on | Expected |
|---|---|---|
| `show interfaces trunk` | all | Trunks up, native VLAN 99, allowed 10,20,30,40,99 |
| `show interfaces fa0/1 switchport` | ASW1 | `Negotiation of Trunking: Off` |

## EtherChannel

| Command | Run on | Expected |
|---|---|---|
| `show etherchannel summary` | DSW1, DSW2 | `Po1(SU)` with `Fa0/23(P)` and `Fa0/24(P)` |
| `show interfaces port-channel 1` | DSW1, DSW2 | up/up |

## Spanning Tree

| Command | Run on | Expected |
|---|---|---|
| `show spanning-tree summary` | all | Mode rapid-pvst |
| `show spanning-tree vlan 10` | DSW1 | "This bridge is the root" |
| `show spanning-tree vlan 30` | DSW2 | "This bridge is the root" |
| `show spanning-tree vlan 10` | ASW1 | One uplink Root/FWD, the other Altn/BLK |
| `show spanning-tree root` | ASW1 | Root IDs match DSW1 / DSW2 |

## HSRP and routing

| Command | Run on | Expected |
|---|---|---|
| `show standby brief` | DSW1 | Active for VLAN 10, 20; Standby for 30, 40 |
| `show standby brief` | DSW2 | Active for VLAN 30, 40; Standby for 10, 20 |
| `ping 192.168.20.10` | PC-IT | Replies via the HSRP gateway |
| `ping 192.168.40.10` | PC-FINANCE | Replies via the HSRP gateway |

## Edge ports

| Command | Run on | Expected |
|---|---|---|
| `show spanning-tree interface fa0/10 portfast` | ASW1-4 | PortFast enabled |
| `show interfaces status err-disabled` | ASW1-4 | Empty unless BPDU Guard fired |
