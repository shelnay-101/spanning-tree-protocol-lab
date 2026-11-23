# 04 - Rapid-PVST+ Root Election and Port Roles

| Field | Value |
|---|---|
| Lab reference | Lab exercise 1: Root election |
| Devices | DSW1, DSW2, ASW1 |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Prove DSW1 is root for VLAN 10 and 20, DSW2 is root for VLAN 30 and 40, no access switch is root, and each access switch blocks one uplink per VLAN.

## Steps

1. Run `show spanning-tree summary` on DSW1.
2. On DSW1 run `show spanning-tree vlan 10` and `show spanning-tree vlan 20`.
3. On DSW2 run `show spanning-tree vlan 30` and `show spanning-tree vlan 40`.
4. On ASW1 run `show spanning-tree vlan 10` and `show spanning-tree vlan 30`.

## Expected result

- Mode is `rapid-pvst`.
- DSW1 shows `This bridge is the root` for VLAN 10 and 20; DSW2 for VLAN 30 and 40.
- On ASW1, VLAN 10 uses the uplink toward DSW1 as Root/FWD and the other as Altn/BLK; VLAN 30 is the opposite.

## Evidence checklist


| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [04-01-dsw1-stp-summary.png](screenshots/04-01-dsw1-stp-summary.png) | Switch is in rapid-pvst mode | ☐ |
| 2 | [04-02-dsw1-stp-vlan10,20.png](screenshots/04-02-dsw1-stp-vlan10,20.png) | This bridge is the root | ☐ |
| 3 | [04-03-dsw2-stp-vlan30,40.png](screenshots/04-03-dsw2-stp-vlan30,40.png) | This bridge is the root | ☐ |
| 4 | [04-04-asw1-stp-vlan10.png](screenshots/04-04-asw1-stp-vlan10.png) | One Root/FWD port and one Altn/BLK port | ☐ |
| 5 | [04-05-asw1-stp-vlan30.png](screenshots/04-05-asw1-stp-vlan30.png) | Port roles opposite to VLAN 10 | ☐ |


