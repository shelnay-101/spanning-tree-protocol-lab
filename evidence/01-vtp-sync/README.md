# 01 - VTP: DSW1 Server, All Others Client

| Field | Value |
|---|---|
| Lab reference | Design feature: VTP v2 |
| Devices | DSW1 (server), DSW2, ASW1-ASW4 (clients) |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Prove DSW1 is the only VTP server, all switches share domain, version and revision, and a VLAN created on DSW1 syncs automatically to every client.

## Steps

1. Run `show vtp status` on all six switches.
2. Run `show vlan brief` on DSW1 and on ASW1.
3. Sync test: on DSW1 enter `configure terminal`, `vlan 50`, `name TEST`, `end`.
4. Wait 30 seconds. Run `show vlan brief` on DSW2 and ASW4. VLAN 50 must be present.
5. Cleanup: on DSW1 enter `no vlan 50`. Confirm VLAN 50 disappears from ASW4.

## Expected result

- DSW1 shows `VTP Operating Mode: Server`; the other five show `Client`.
- Domain `ENTERPRISE` and version 2 everywhere; configuration revision is identical.
- VLANs 10, 20, 30, 40, 99, 999 are present on every switch.
- VLAN 50 appears on clients after being created on DSW1 and disappears after deletion.

## Evidence checklist

| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [01-01-dsw1-show-vtp-status.png](screenshots/01-01-dsw1-show-vtp-status.png) | Mode Server, domain ENTERPRISE, revision number | ☐ |
| 2 | [01-02-dsw2-show-vtp-status.png](screenshots/01-02-dsw2-show-vtp-status.png) | Mode Client, same domain and revision | ☐ |
| 3 | [01-03-asw1-show-vtp-status.png](screenshots/01-03-asw1-show-vtp-status.png) | Mode Client | ☐ |
| 4 | [01-04-asw2-show-vtp-status.png](screenshots/01-04-asw2-show-vtp-status.png) | Mode Client | ☐ |
| 5 | [01-05-asw3-show-vtp-status.png](screenshots/01-05-asw3-show-vtp-status.png) | Mode Client | ☐ |
| 6 | [01-06-asw4-show-vtp-status.png](screenshots/01-06-asw4-show-vtp-status.png) | Mode Client | ☐ |
| 7 | [01-07-dsw1-show-vlan-brief.png](screenshots/01-07-dsw1-show-vlan-brief.png) | VLANs 10, 20, 30, 40, 99, 999 | ☐ |
| 8 | [01-08-asw1-show-vlan-brief.png](screenshots/01-08-asw1-show-vlan-brief.png) | Same VLANs learned via VTP | ☐ |
| 9 | [01-09-dsw1-create-vlan-50.png](screenshots/01-09-dsw1-create-vlan-50.png) | VLAN 50 being created on DSW1 | ☐ |
| 10 | [01-10-dsw2-vlan-50-appeared.png](screenshots/01-10-dsw2-vlan-50-appeared.png) | VLAN 50 visible on DSW2 | ☐ |
| 11 | [01-11-asw4-vlan-50-appeared.png](screenshots/01-11-asw4-vlan-50-appeared.png) | VLAN 50 visible on ASW4 | ☐ |
| 12 | [01-12-asw4-vlan-50-removed.png](screenshots/01-12-asw4-vlan-50-removed.png) | VLAN 50 gone after deletion on DSW1 | ☐ |


