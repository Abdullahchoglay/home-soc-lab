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

The endpoint event was first verified locally on 2026-09-17. On 2026-10-29,
failed-logon auditing was confirmed, a new controlled failure was generated,
and Event ID 4625 was verified in the Wazuh `wazuh-alerts-*` index for
`WIN-ENDPOINT-01`.

## Analyst Guidance

Review the target account, source device/address, logon type, failure reason,
frequency, and surrounding successful logons. Repeated failures across accounts
or from an unusual source should be escalated.
