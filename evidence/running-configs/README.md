# Running Configurations

After the lab is fully configured and **before** you start the tests, export the configuration of every device. This proves what was actually configured when the tests were run.

## How

On each device open the CLI and run:

```
enable
terminal length 0
show running-config
```

Copy the output into a text file and save it here with these names:

| File | Device |
|---|---|
| `DSW1-running-config.txt` | DSW1 |
| `DSW2-running-config.txt` | DSW2 |
| `ASW1-running-config.txt` | ASW1 |
| `ASW2-running-config.txt` | ASW2 |
| `ASW3-running-config.txt` | ASW3 |
| `ASW4-running-config.txt` | ASW4 |

Tip: compare each file with the matching file in `../../configs/` to show the lab matches the design.
