# 04 - Apply Order

VTP only syncs over working trunks and only when domain and password match, so
the order matters.

## Steps

1. Build the topology and cable it using [03-link-map.md](03-link-map.md).
2. Paste [../configs/DSW1.txt](../configs/DSW1.txt). DSW1 is the VTP server and creates all VLANs.
3. Paste [../configs/DSW2.txt](../configs/DSW2.txt).
4. Paste ASW1-ASW4: [ASW1](../configs/ASW1.txt), [ASW2](../configs/ASW2.txt), [ASW3](../configs/ASW3.txt), [ASW4](../configs/ASW4.txt).
5. Wait 30-60 seconds, then run `show vlan brief` on a client to confirm VLANs arrived.
6. Paste [../configs/post-vtp-sync.txt](../configs/post-vtp-sync.txt) on DSW2 and re-enter any access-switch commands that errored.
7. Set the PC IP addresses from [02-addressing-plan.md](02-addressing-plan.md).
8. Verify with [../verification/verification-commands.md](../verification/verification-commands.md).

## Why some commands may error on the first paste

Clients do not know VLANs 10, 20, 30, 40, 99 and 999 until VTP syncs. These
commands can fail if pasted too early:

- `switchport access vlan 10/20/30/40/999` on the access switches
- `spanning-tree vlan 10,20,30,40,99 priority ...` on DSW2

Re-enter them after the sync. This is normal, not a mistake in the config.

## If VTP does not sync

- Check that trunks are up: `show interfaces trunk`
- Check domain and password match: `show vtp status`
- Check VTP version 2 on every switch
- Make sure the server revision number is higher than the clients
- Reset a reused switch first: delete `vlan.dat`, then reload
