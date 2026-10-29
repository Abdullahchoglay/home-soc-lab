# Reproduction Guide

This guide records the lab workflow at a high level. Package versions and
commands should be checked against current official documentation before a new
deployment.

## Prerequisites

- Windows 11 host
- VirtualBox
- Ubuntu Server 24.04 LTS VM
- Sufficient memory and disk space for an all-in-one Wazuh deployment
- Administrator access on Windows
- `sudo` access on Ubuntu

## 1. Deploy the Wazuh server

1. Create the Ubuntu Server VM.
2. Update Ubuntu and verify time synchronization.
3. Install the Wazuh manager, indexer, and dashboard using the official
   all-in-one installation procedure.
4. Confirm each service is running and sign in to the dashboard.

Do not publish installer output because it may contain generated credentials.

## 2. Configure host-to-guest networking

This lab retained VirtualBox NAT for the Ubuntu VM. Localhost-only forwarding
was used for agent communication:

| Host endpoint | Guest endpoint | Purpose |
|---|---|---|
| `127.0.0.1:1514/TCP` | `10.0.2.15:1514/TCP` | Agent events |
| `127.0.0.1:1515/TCP` | `10.0.2.15:1515/TCP` | Agent enrollment |

The guest address is lab-specific and should not be copied blindly.

## 3. Enroll the Windows endpoint

1. Download the current Wazuh Windows agent from the official package source.
2. Validate the Authenticode signature before installation.
3. Configure the manager and registration address for the chosen network.
4. Assign a clear agent name such as `WIN-ENDPOINT-01`.
5. Start the Wazuh service and confirm the dashboard reports the agent active.

## 4. Validate File Integrity Monitoring

1. Confirm the selected directory is monitored in real time.
2. Create a clearly labelled harmless text file.
3. Wait for collection, modify the file, wait again, and delete it.
4. Confirm rules 554, 550, and 553 in Wazuh.
5. Record timestamps, path, hashes, rule levels, and the authorization context.

## 5. Validate Windows authentication telemetry

1. Use a nonexistent lab account to generate one controlled failure.
2. Confirm Windows Security Event ID 4625.
3. Review logon type, failure reason, status, source, and surrounding events.
4. Confirm ingestion and alerting in Wazuh before marking the detection complete.

Avoid repeated failures against real accounts because account-lockout policies
may apply.

## 6. Validate PowerShell telemetry

1. Enable script-block and module logging.
2. Add `Microsoft-Windows-PowerShell/Operational` to Wazuh event-channel
   collection.
3. Back up and validate the agent configuration before restarting the service.
4. Run a harmless uniquely marked command.
5. Confirm Event ID 4104 locally and then verify manager-side ingestion.

## 7. Document and preserve

1. Remove or sanitize local identifiers from evidence.
2. Record limitations and pending validation honestly.
3. Commit only reviewed files.
4. Create a VM snapshot when adequate disk space is available.