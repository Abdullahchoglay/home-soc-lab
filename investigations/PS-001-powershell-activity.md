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
- **Custom rule:** 100101, level 5
- **MITRE ATT&CK:** T1059.001 — PowerShell
- **Wazuh rule-engine verification:** Passed on 2026-10-29
- **Live endpoint-forwarded Rule 100101 hit:** Pending final confirmation

## Analysis

The marker and timestamp match the authorized test. Event ID 4104 confirms
that PowerShell script-block logging recorded the activity locally. The Wazuh
agent was configured to collect the PowerShell Operational channel. A sanitized
equivalent event was decoded by Wazuh 4.14.7 and matched custom rule 100101;
`wazuh-logtest` reported that an alert would be generated. The final live event
hop has not yet been demonstrated as a Rule 100101 alert in Discover.

PowerShell activity is relevant to MITRE ATT&CK T1059.001, but this harmless
test does not represent malicious execution.

## Verdict

**Benign true positive at the Windows event layer, with manager-side rule logic
verified.** Live end-to-end Rule 100101 alerting remains the only open check.

## Response

No containment was required. In a real investigation, review the complete
script block, user and process context, encoded commands, downloads, security
control changes, and related network activity.

## Follow-up

Generate a fresh unique marker and retain a sanitized Wazuh Discover result that
shows Rule 100101, the agent, timestamp, and script-block marker.
