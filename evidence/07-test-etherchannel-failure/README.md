# 07 - Test: EtherChannel Member and Bundle Failure

| Field | Value |
|---|---|
| Lab reference | Lab exercise 3: EtherChannel failure |
| Devices | DSW1, DSW2, ASW1, PC-IT, PC-FINANCE |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Show the bundle survives one member failure without disruption and what happens when both members fail (the DSWs then reach each other through the access switches).

## Steps

1. Run `show etherchannel summary` on DSW1 (baseline) and start `ping -t 192.168.30.10` from PC-IT.
2. On DSW1 enter `interface fa0/23`, `shutdown`. Run `show etherchannel summary` again.
3. Observe the ping. Run `show spanning-tree vlan 10` on DSW2 and compare with the baseline.
4. On DSW1 also shut `fa0/24`. Run `show etherchannel summary`.
5. Run `show spanning-tree vlan 10` on DSW2 and `show standby brief` on both DSWs. Note which port now leads to the root (an access-switch-facing port).
6. Restore: `no shutdown` on Fa0/23 and Fa0/24. Confirm Po1(SU) with both members (P).

## Expected result

- One member down: `Po1(SU)` with `Fa0/23(D)` and `Fa0/24(P)`; pings keep working; STP unchanged.
- Both members down: `Po1(SD)`; STP reconverges and the DSWs reach each other through an access switch; pings recover after a short interruption.
- After restoring, the bundle returns to `Po1(SU)` with both ports (P).

## Evidence checklist

| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [07-01-dsw1-etherchannel-summary-before.png](screenshots/07-01-dsw1-etherchannel-summary-before.png) | Baseline Po1(SU) both ports bundled | ☐ |
| 2 | [07-02-dsw1-shutdown-fa0-23.png](screenshots/07-02-dsw1-shutdown-fa0-23.png) | Fa0/23 shut down | ☐ |
| 3 | [07-03-dsw1-etherchannel-summary-one-down.png](screenshots/07-03-dsw1-etherchannel-summary-one-down.png) | Po1 still up with one member | ☐ |
| 4 | [07-04-pc-it-ping-one-down.png](screenshots/07-04-pc-it-ping-one-down.png) | Ping unaffected | ☐ |
| 5 | [07-05-dsw1-etherchannel-summary-both-down.png](screenshots/07-05-dsw1-etherchannel-summary-both-down.png) | Po1(SD) | ☐ |
| 6 | [07-06-dsw2-stp-vlan10-both-down.png](screenshots/07-06-dsw2-stp-vlan10-both-down.png) | New root port after bundle failure | ☐ |
| 7 | [07-07-dsw1-etherchannel-summary-restored.png](screenshots/07-07-dsw1-etherchannel-summary-restored.png) | Po1(SU) with both ports (P) | ☐ |


