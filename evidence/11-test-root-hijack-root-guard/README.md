# 11 - Test: Root Bridge Hijack and Root Guard

| Field | Value |
|---|---|
| Lab reference | Lab exercise 7: Root hijack |
| Devices | ASW1 (attacker), DSW1, DSW2 |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Show an access switch with priority 0 can steal the root role, and Root Guard prevents it.

## Steps

1. Baseline: `show spanning-tree vlan 10` on DSW1 (root).
2. On ASW1 enter `spanning-tree vlan 10 priority 0`. Wait 30 seconds.
3. Run `show spanning-tree vlan 10` on DSW1 and DSW2. Root should now be ASW1.
4. Undo: on ASW1 `no spanning-tree vlan 10 priority`. Confirm DSW1 is root again.
5. Protect: on DSW1 and DSW2 enter `interface range fa0/2 - 5` then `spanning-tree guard root`.
6. Repeat the attack on ASW1 (`spanning-tree vlan 10 priority 0`).
7. On DSW1 run `show spanning-tree inconsistentports` and `show spanning-tree vlan 10`.
8. Cleanup: on ASW1 `no spanning-tree vlan 10 priority`; check ports recover to normal.

## Expected result

- Without Root Guard, ASW1 becomes root for VLAN 10.
- With Root Guard, the DSW ports facing ASW1 become `root-inconsistent` and DSW1 stays root.
- After cleanup the ports recover automatically.

## Evidence checklist

| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [11-01-dsw1-stp-vlan10-baseline.png](screenshots/11-01-dsw1-stp-vlan10-baseline.png) | DSW1 is root | ☐ |
| 2 | [11-02-asw1-set-priority-0.png](screenshots/11-02-asw1-set-priority-0.png) | Priority 0 command on ASW1 | ☐ |
| 3 | [11-03-dsw1-stp-vlan10-hijacked.png](screenshots/11-03-dsw1-stp-vlan10-hijacked.png) | Root is now ASW1 | ☐ |
| 4 | [11-04-dsw2-stp-vlan10-hijacked.png](screenshots/11-04-dsw2-stp-vlan10-hijacked.png) | DSW2 also sees ASW1 as root | ☐ |
| 5 | [11-05-dsw1-configure-guard-root.png](screenshots/11-05-dsw1-configure-guard-root.png) | Root Guard configuration | ☐ |
| 6 | [11-06-dsw1-inconsistentports.png](screenshots/11-06-dsw1-inconsistentports.png) | Root-inconsistent port listed | ☐ |



