# Evidence Project

This folder is the proof that the lab works. For every feature and test there is one folder with a
test sheet (`README.md`) and a `screenshots/` folder. Build the lab, run each test, save the screenshots
with the exact file names listed in each sheet, and fill in the results.

## Folder structure

```
evidence/
├── README.md
├── TEST-REPORT.md
├── running-configs/
│   └── README.md
├── 00-baseline-topology-cabling/
│   ├── README.md
│   └── screenshots/
├── 01-vtp-sync/
│   ├── README.md
│   └── screenshots/
├── 02-trunks-dtp-disabled/
│   ├── README.md
│   └── screenshots/
├── 03-etherchannel-lacp/
│   ├── README.md
│   └── screenshots/
├── 04-stp-root-election/
│   ├── README.md
│   └── screenshots/
├── 05-hsrp-inter-vlan/
│   ├── README.md
│   └── screenshots/
├── 06-test-rapid-convergence/
│   ├── README.md
│   └── screenshots/
├── 07-test-etherchannel-failure/
│   ├── README.md
│   └── screenshots/
├── 08-test-etherchannel-misconfig/
│   ├── README.md
│   └── screenshots/
├── 09-test-dtp-behavior/
│   ├── README.md
│   └── screenshots/
├── 10-test-bpdu-guard/
│   ├── README.md
│   └── screenshots/
├── 11-test-root-hijack-root-guard/
│   ├── README.md
│   └── screenshots/
├── 12-test-vtp-revision-overwrite/
│   ├── README.md
│   └── screenshots/
└── 13-test-hsrp-failover/
    ├── README.md
    └── screenshots/
```

## Workflow

1. Build the topology and apply the configs (see `../docs/04-apply-order.md`).
2. Save the Packet Tracer file as `../packet-tracer/enterprise-stp-lab.pkt`.
3. Export all running configs into `running-configs/` (see its README).
4. Do the tests in order, **00 first**. For each test:
   1. Open its `README.md` and read the steps.
   2. Run the commands and take the screenshots.
   3. Save every screenshot in that test's `screenshots/` folder using the exact file name from the checklist.
   4. Paste key CLI output into **Actual result**, write **Observations**, tick the **Result**.
5. Update the status in `TEST-REPORT.md`.
6. Commit and push.

## Screenshot rules

- Show the device prompt (hostname), the command typed and its full output.
- Show the whole Packet Tracer window title or CLI window so the device is identifiable.
- Use PNG format.
- One screenshot per checklist item. Do not rename files; the sheets link to the exact names.
- Take before and after screenshots for every failure test.
- For long output, set `terminal length 0` first so nothing is cut off with `--More--`.

Capture shortcuts: Windows `Win + Shift + S`, macOS `Cmd + Shift + 4`, Linux use your screenshot tool.

## Naming convention

`<test number>-<item number>-<device>-<what>.png`

Example: `04-06-asw1-stp-vlan10.png` means test 04, item 6, device ASW1, `show spanning-tree vlan 10`.

## Final checklist before you push

- [ ] All ☐ in every test sheet are ✅
- [ ] Every `screenshots/` folder contains the listed files
- [ ] `TEST-REPORT.md` statuses and overall conclusion filled in
- [ ] Running configs saved in `running-configs/`
- [ ] The `.pkt` file saved in `../packet-tracer/`
- [ ] Test 12 was done on a copy and the original `.pkt` is unchanged
- [ ] `LICENSE` has your name
