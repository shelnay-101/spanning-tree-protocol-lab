# STP / EtherChannel Simulation Exercises

Run these after the base lab is verified.

## 1. Root election
Run `show spanning-tree vlan 10` on every switch. Identify root ports, designated
ports and alternate ports. Each access switch should forward VLAN 10 and 20 toward
DSW1 and VLAN 30 and 40 toward DSW2, with the other uplink Alternate (blocking).

## 2. Rapid convergence
Start `ping -t` from PC-IT to PC-HR, then shut DSW1 Fa0/2. Failover should take
about 1-2 seconds with Rapid-PVST+, compared with roughly 30-50 seconds on classic STP.

## 3. EtherChannel member failure
Shut DSW1 Fa0/23. Po1 stays up on Fa0/24 and STP does not change. Then shut both
members: Po1 goes down and the DSWs reach each other through the access switches,
so STP reconverges over an access-switch path.

## 4. EtherChannel misconfiguration
Change one side to `channel-group 1 mode on` while the other stays `active`.
The channel will not form. This shows static mode and LACP do not interoperate.

## 5. DTP behavior
On one side of a link only, set `switchport mode dynamic desirable` and compare
with the `nonegotiate` setting. Restore `switchport nonegotiate` afterwards.

## 6. BPDU Guard
Connect a switch to ASW1 Fa0/10. The port goes err-disabled. Recover with
`shutdown` followed by `no shutdown` after removing the switch.

## 7. Root hijack and Root Guard
Set ASW1 priority to 0 for VLAN 10 and watch the root move to ASW1. Fix it by
resetting the priority and adding `spanning-tree guard root` on the DSW ports
facing the access switches.

## 8. VTP revision overwrite
On a spare switch, create and delete VLANs to raise its configuration revision,
set the same domain and password, and connect it as a client or server. A higher
revision overwrites the VLAN database. Reset reused switches before connecting them.

## 9. HSRP failover
Shut DSW1 and confirm DSW2 becomes active for VLAN 10 and 20 and keeps answering
on the virtual gateway address.
