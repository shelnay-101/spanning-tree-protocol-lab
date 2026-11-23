# 10 - Test: PortFast and BPDU Guard on an Edge Port

| Field | Value |
|---|---|
| Lab reference | Lab exercise 6: BPDU Guard |
| Devices | ASW1, PC-IT, one spare 2960 (SW-ROGUE) |
| Tester | |
| Date / time | |
| Packet Tracer version | |
| Result | ☐ Pass &nbsp; ☐ Fail |

## Objective

Show an access port with BPDU Guard shuts itself down when a switch is plugged in.

## Steps

1. On ASW1 run `show running-config interface fa0/10` and `show spanning-tree interface fa0/10 portfast`.
2. Unplug PC-IT. Add a spare 2960 named SW-ROGUE and cable it to ASW1 Fa0/10.
3. Wait about 10-30 seconds. Capture the log message on ASW1.
4. Run `show interfaces status err-disabled` and `show interfaces fa0/10`.
5. Remove SW-ROGUE and reconnect PC-IT to Fa0/10.
6. Recover: on ASW1 `interface fa0/10`, `shutdown`, `no shutdown`. Ping the gateway from PC-IT.

## Expected result

- Fa0/10 shows PortFast and BPDU Guard enabled.
- After SW-ROGUE connects, a `BPDUGUARD` message appears and the port is `err-disabled`.
- After recovery PC-IT works again.

## Evidence checklist

| # | File | Must show | Captured |
|---|---|---|---|
| 1 | [10-01-asw1-status-err-disabled.png](screenshots/10-01-asw1-status-err-disabled.png) | Fa0/10 in err-disabled | ☐ |
