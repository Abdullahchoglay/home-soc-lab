# Home SOC Lab — Build Log

## Objective

Build a small personal SOC environment for practicing security monitoring,
log analysis, alert triage, and incident investigation.

## Host

- Operating System: Windows 11
- RAM: 16 GB
- Virtualization: VirtualBox
- CPU: Intel Pentium Gold 6405U

## SOC Server

- Operating System: Ubuntu Server 24.04 LTS
- Virtualization Platform: VirtualBox
- SIEM: Wazuh

## Current Progress

- [x] VirtualBox installed
- [x] Ubuntu Server VM created
- [x] Ubuntu Server installed
- [x] Successfully logged into Ubuntu
- [x] Install Wazuh
- [x] Connect Windows endpoint `WIN-ENDPOINT-01`
- [x] Generate harmless file-integrity events
- [x] Investigate first FIM alerts
- [x] Document investigation FIM-001
- [x] Generate controlled Windows failed-logon event (4625)
- [x] Enable PowerShell script-block and module logging
- [x] Collect the PowerShell Operational event channel with Wazuh
- [x] Generate controlled PowerShell script-block event (4104)
- [ ] Verify AUTH-001 and PS-001 in the Wazuh manager
- [ ] Install Sysmon after resolving host storage constraints

## Notes

The Ubuntu server will act as the central security monitoring/SIEM
component of the lab.

The build required troubleshooting unsupported software, insufficient disk
space, incorrect VM time, an invalid Windows installer, administrator
permissions, and VirtualBox NAT reachability. These issues and their resolutions
are recorded in `troubleshooting.md`.

## Endpoint Enrollment

The Windows endpoint was enrolled as `WIN-ENDPOINT-01`. The Wazuh dashboard
confirmed that the agent was connected and active.

## Detection Test 01 — File Integrity Monitoring

A harmless text file named `wazuh-fim-lab-test.txt` was created, modified, and
deleted in the monitored Windows Startup directory. The expected Wazuh rule IDs
are 554 (file added), 550 (file modified), and 553 (file deleted).