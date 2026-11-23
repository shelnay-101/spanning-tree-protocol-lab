# 02 - Trunks and DTP Disabled

| Field | Value |
|---|---|
| Lab reference | Design feature: DTP disabled |
| Devices | DSW1, DSW2, ASW1, ASW4 (and any other switch you want to include) |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Prove every inter-switch link is a static 802.1Q trunk with native VLAN 99, and DTP negotiation is off.

## Steps

1. Run `show interfaces trunk` on DSW1, DSW2, ASW1 and ASW4.
2. On ASW1 run `show interfaces fa0/1 switchport`.
3. On DSW1 run `show interfaces fa0/2 switchport`.
4. On ASW1 run `show interfaces fa0/10 switchport` (the PC access port).

## Expected result

- Trunk ports show mode `on`, encapsulation 802.1q, native VLAN 99.
- Allowed VLANs are 10, 20, 30, 40, 99.
- Trunk ports show `Negotiation of Trunking: Off`.
- PC port shows `Administrative Mode: static access` and VLAN 10.

## Evidence checklist

Save each screenshot in the `screenshots/` folder with exactly the file name below. Each screenshot must show the device prompt (hostname), the command and its output. Replace ☐ with ✅ once captured.

| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [02-01-dsw1-show-interfaces-trunk.png](screenshots/02-01-dsw1-show-interfaces-trunk.png) | Fa0/2-5 and Po1 trunking, native 99 | ☐ |
| 2 | [02-02-dsw2-show-interfaces-trunk.png](screenshots/02-02-dsw2-show-interfaces-trunk.png) | Fa0/2-5 and Po1 trunking, native 99 | ☐ |
| 3 | [02-03-asw1-show-interfaces-trunk.png](screenshots/02-03-asw1-show-interfaces-trunk.png) | Fa0/1 and Fa0/2 trunking | ☐ |
| 4 | [02-04-asw4-show-interfaces-trunk.png](screenshots/02-04-asw4-show-interfaces-trunk.png) | Fa0/1 and Fa0/2 trunking | ☐ |
| 5 | [02-05-asw1-fa0-1-switchport.png](screenshots/02-05-asw1-fa0-1-switchport.png) | Negotiation of Trunking: Off | ☐ |
| 6 | [02-06-dsw1-fa0-2-switchport.png](screenshots/02-06-dsw1-fa0-2-switchport.png) | Negotiation of Trunking: Off | ☐ |
| 7 | [02-07-asw1-fa0-10-switchport.png](screenshots/02-07-asw1-fa0-10-switchport.png) | Static access, VLAN 10 | ☐ |

## Actual result

Paste the key CLI output here:

```text

```

## Observations

Write what you saw, and explain any difference from the expected result.

## Conclusion

☐ Expected result achieved &nbsp; ☐ Not achieved (explain above)
