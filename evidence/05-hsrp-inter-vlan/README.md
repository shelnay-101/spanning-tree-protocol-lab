# 05 - HSRP Gateways and Inter-VLAN Routing

| Field | Value |
|---|---|
| Lab reference | Design feature: HSRP v2 aligned with STP |
| Devices | DSW1, DSW2, all PCs |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Prove DSW1 is HSRP active for VLAN 10 and 20, DSW2 for VLAN 30 and 40, and PCs reach each other across VLANs.

## Steps

1. Run `show standby brief` on DSW1 and DSW2.
2. Run `show ip interface brief` on DSW1.
3. From PC-IT run: `ping 192.168.10.1` (gateway).
4. From PC-IT ping PC-SALES (`ping 192.168.20.10`), PC-FINANCE (`ping 192.168.30.10`) and PC-HR (`ping 192.168.40.10`).
5. From PC-IT run `tracert 192.168.40.10`.

## Expected result

- DSW1 is Active for VLAN 10 and 20 and Standby for 30 and 40; DSW2 is the reverse.
- All pings succeed. The first ping may time out while ARP resolves; run it again.
- The first hop of the traceroute is the active HSRP router for the source VLAN.

## Evidence checklist


| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [05-01-dsw1-standby-brief.png](screenshots/05-01-dsw1-standby-brief.png) | Active for VLAN 10, 20; Standby for 30, 40 | ☐ |
| 2 | [05-02-dsw2-standby-brief.png](screenshots/05-02-dsw2-standby-brief.png) | Active for VLAN 30, 40; Standby for 10, 20 | ☐ |
| 3 | [05-03-dsw1-ip-interface-brief.png](screenshots/05-03-dsw1-ip-interface-brief.png) | SVIs for VLAN 10, 20, 30, 40, 99 up/up | ☐ |
| 4 | [05-04-pc-it-ping-gateway.png](screenshots/05-04-pc-it-ping-gateway.png) | Replies from 192.168.10.1 | ☐ |
| 5 | [05-05-pc-it-ping-pc-sales.png](screenshots/05-05-pc-it-ping-pc-sales.png) | Replies from 192.168.20.10 | ☐ |
| 6 | [05-06-pc-it-ping-pc-finance.png](screenshots/05-06-pc-it-ping-pc-finance.png) | Replies from 192.168.30.10 | ☐ |
| 7 | [05-07-pc-it-ping-pc-hr.png](screenshots/05-07-pc-it-ping-pc-hr.png) | Replies from 192.168.40.10 | ☐ |
| 8 | [05-08-pc-it-tracert-pc-hr.png](screenshots/05-08-pc-it-tracert-pc-hr.png) | Hop list to 192.168.40.10 | ☐ |


