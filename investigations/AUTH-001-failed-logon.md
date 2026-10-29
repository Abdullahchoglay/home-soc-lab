# Investigation AUTH-001 — Controlled Failed Logon

## Summary

A controlled authentication failure was generated on `WIN-ENDPOINT-01` using
the nonexistent account `SOC-LAB-INVALID`.

## Evidence

- **Timestamp:** 2026-09-17 16:21:20 UTC
- **Provider:** Microsoft-Windows-Security-Auditing
- **Event ID:** 4625
- **Logon type:** 2 (interactive)
- **Failure:** Unknown user name or bad password
- **Status/sub-status:** `0xC000006D` / `0xC0000064`
- **Logon result:** Failed as intended

## Analysis

The event time and fake account match the authorized test. There was one
controlled attempt, no real account was targeted, and no successful logon
followed from the test. This is useful telemetry for detecting password attacks,
but a single known lab event does not indicate compromise.

## Verdict

**Benign true positive at the Windows event layer.** Wazuh manager-side alert
verification remains pending.

## Response

No containment was required. In a real investigation, the analyst should check
for repeated failures, successful follow-on logons, unusual source addresses,
and targeting of privileged accounts.