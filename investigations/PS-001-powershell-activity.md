# Investigation PS-001 — Controlled PowerShell Activity

## Summary

A harmless PowerShell command containing the marker `SOC-LAB-PS-001` was run on
`WIN-ENDPOINT-01` to validate script-block telemetry.

## Evidence

- **Timestamp:** 2026-09-17 16:34:42 UTC
- **Provider:** Microsoft-Windows-PowerShell
- **Event ID:** 4104
- **Marker:** `SOC-LAB-PS-001`
- **Source:** Local Windows PowerShell Operational event log
- **Wazuh manager verification:** Pending

## Analysis

The marker and timestamp match the authorized test. Event ID 4104 confirms
that PowerShell script-block logging recorded the activity locally. The Wazuh
agent was configured to collect the PowerShell Operational channel, but the
event has not yet been confirmed in the Wazuh dashboard or manager alerts.

PowerShell activity is relevant to MITRE ATT&CK T1059.001, but this harmless
test does not represent malicious execution.

## Verdict

**Benign true positive at the Windows event layer.** End-to-end Wazuh ingestion
remains unverified.

## Response

No containment was required. In a real investigation, review the complete
script block, user and process context, encoded commands, downloads, security
control changes, and related network activity.

## Follow-up

Search the Wazuh dashboard or manager alerts for Event ID 4104, the endpoint,
timestamp, and unique marker before marking PS-001 complete.
