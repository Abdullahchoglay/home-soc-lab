# Detection AUTH-001 — Windows Failed Interactive Logon

## Objective

Identify unsuccessful interactive Windows authentication attempts that may
represent mistyped credentials, account discovery, or password attacks.

## Data Source

Windows Security event log collected from `WIN-ENDPOINT-01`.

## Event

- **Windows Event ID:** 4625
- **Logon type:** 2 (interactive)
- **Test account:** `SOC-LAB-INVALID`
- **Failure reason:** Unknown user name or bad password
- **Status:** `0xC000006D`
- **Sub-status:** `0xC0000064`

## Validation Status

The endpoint event was regenerated and verified locally on 2026-09-17. Wazuh
manager-side alert verification is pending because VirtualBox Guest Control
stopped accepting new Ubuntu sessions during validation.

## Analyst Guidance

Review the target account, source device/address, logon type, failure reason,
frequency, and surrounding successful logons. Repeated failures across accounts
or from an unusual source should be escalated.