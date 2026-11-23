# 06 - Test: Rapid-PVST+ Convergence After a Link Failure

| Field | Value |
|---|---|
| Lab reference | Lab exercise 2: Rapid convergence |
| Devices | PC-IT, PC-HR, ASW1, DSW1 |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Measure how quickly traffic recovers when the active uplink of ASW1 fails.

## Steps

1. On ASW1 run `show spanning-tree vlan 10` and note the Root port (expected Fa0/1 toward DSW1).
2. On PC-IT start a continuous ping: `ping -t 192.168.40.10`. Leave it running.
3. On DSW1 enter `configure terminal`, `interface fa0/2`, `shutdown`.
4. Watch the ping window, then press Ctrl+C and screenshot the statistics.
5. On ASW1 run `show spanning-tree vlan 10` again. The Root port should now be Fa0/2 toward DSW2.
6. Restore: on DSW1 `interface fa0/2`, `no shutdown`.

## Expected result

- Only a few packets are lost (typically 1-3), then replies resume.
- ASW1 root port moves to the uplink toward DSW2.
- Recovery is far quicker than the 30-50 seconds of classic 802.1D.

## Evidence checklist

| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [06-01-asw1-stp-vlan10-before.png](screenshots/06-01-asw1-stp-vlan10-before.png) | Root port before failure | ☐ |
| 2 | [06-02-pc-it-ping-running.png](screenshots/06-02-pc-it-ping-running.png) | Continuous ping running with replies | ☐ |
| 3 | [06-03-dsw1-shutdown-fa0-2.png](screenshots/06-03-dsw1-shutdown-fa0-2.png) | Interface Fa0/2 being shut down on DSW1 | ☐ |
| 4 | [06-04-pc-it-ping-statistics.png](screenshots/06-04-pc-it-ping-statistics.png) | Packets sent/received/lost after the failure | ☐ |
| 5 | [06-05-asw1-stp-vlan10-after.png](screenshots/06-05-asw1-stp-vlan10-after.png) | Root port moved to the other uplink | ☐ |
| 6 | [06-06-dsw1-restore-fa0-2.png](screenshots/06-06-dsw1-restore-fa0-2.png) | Interface re-enabled | ☐ |

## Notes

Packet Tracer timing is a simulation. Record the number of lost packets you actually observe rather than an exact time.


