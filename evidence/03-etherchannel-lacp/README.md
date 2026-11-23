# 03 - EtherChannel (LACP) between DSW1 and DSW2

| Field | Value |
|---|---|
| Lab reference | Design feature: EtherChannel |
| Devices | DSW1, DSW2 |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Prove Fa0/23 and Fa0/24 are bundled into Port-channel 1 using LACP and the bundle carries the trunk.

## Steps

1. Run `show etherchannel summary` on DSW1 and DSW2.
2. Run `show interfaces port-channel 1` on DSW1.
3. Run `show interfaces trunk` on DSW1 and confirm Po1 is listed.

## Expected result

- `Po1(SU)` with protocol `LACP`.
- `Fa0/23(P)` and `Fa0/24(P)` bundled on both switches.
- Port-channel 1 is up/up and trunking VLANs 10, 20, 30, 40, 99.

## Evidence checklist

| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [03-01-dsw1-etherchannel-summary.png](screenshots/03-01-dsw1-etherchannel-summary.png) | Po1(SU), LACP, Fa0/23(P) Fa0/24(P) | ☐ |
| 2 | [03-02-dsw2-etherchannel-summary.png](screenshots/03-02-dsw2-etherchannel-summary.png) | Po1(SU), LACP, Fa0/23(P) Fa0/24(P) | ☐ |
| 3 | [03-03-dsw1-show-interfaces-port-channel-1.png](screenshots/03-03-dsw1-show-interfaces-port-channel-1.png) | up/up status | ☐ |
| 4 | [03-04-dsw1-run-interface-port-channel-1.png](screenshots/03-04-dsw1-run-interface-port-channel-1.png) | Port-channel trunk configuration | ☐ |
| 5 | [03-05-dsw1-show-interfaces-trunk-po1.png](screenshots/03-05-dsw1-show-interfaces-trunk-po1.png) | Po1 in the trunk list | ☐ |


