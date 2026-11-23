# 00 - Baseline: Topology, Cabling and IP Addressing

| Field | Value |
|---|---|
| Lab reference | Prerequisite (run before every other test) |
| Devices | All switches and all PCs |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Prove the built topology matches the design and every PC has the correct IP settings.

## Steps

1. Screenshot the whole Packet Tracer workspace with all devices, names and links visible. Wait until all link lights are green.
2. On every switch run `show cdp neighbors` and screenshot the output.
3. On every PC open Desktop > Command Prompt and run `ipconfig`.

## Expected result

- All links are up (green) after STP converges.
- CDP neighbors on each switch match `docs/03-link-map.md`.
- Each PC has the IP, mask and gateway from `docs/02-addressing-plan.md`.

## Evidence checklist

| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [00-01-topology-overview.png](screenshots/00-01-topology-overview.png) | Whole workspace, all devices and links visible | ☐ |
| 2 | [00-02-dsw1-cdp-neighbors.png](screenshots/00-02-dsw1-cdp-neighbors.png) | `show cdp neighbors` on DSW1 (DSW2, ASW1-4) | ☐ |
| 3 | [00-03-dsw2-cdp-neighbors.png](screenshots/00-03-dsw2-cdp-neighbors.png) | `show cdp neighbors` on DSW2 (DSW1, ASW1-4) | ☐ |
| 4 | [00-04-asw1-cdp-neighbors.png](screenshots/00-04-asw1-cdp-neighbors.png) | `show cdp neighbors` on ASW1 (DSW1, DSW2) | ☐ |
| 5 | [00-05-asw2-cdp-neighbors.png](screenshots/00-05-asw2-cdp-neighbors.png) | `show cdp neighbors` on ASW2 | ☐ |
| 6 | [00-06-asw3-cdp-neighbors.png](screenshots/00-06-asw3-cdp-neighbors.png) | `show cdp neighbors` on ASW3 | ☐ |
| 7 | [00-07-asw4-cdp-neighbors.png](screenshots/00-07-asw4-cdp-neighbors.png) | `show cdp neighbors` on ASW4 | ☐ |
| 8 | [00-08-pc-it-ipconfig.png](screenshots/00-08-pc-it-ipconfig.png) | `ipconfig` on PC-IT (192.168.10.10, gw .1) | ☐ |
| 9 | [00-09-pc-sales-ipconfig.png](screenshots/00-09-pc-sales-ipconfig.png) | `ipconfig` on PC-SALES (192.168.20.10, gw .1) | ☐ |
| 10 | [00-10-pc-finance-ipconfig.png](screenshots/00-10-pc-finance-ipconfig.png) | `ipconfig` on PC-FINANCE (192.168.30.10, gw .1) | ☐ |
| 11 | [00-11-pc-hr-ipconfig.png](screenshots/00-11-pc-hr-ipconfig.png) | `ipconfig` on PC-HR (192.168.40.10, gw .1) | ☐ |

