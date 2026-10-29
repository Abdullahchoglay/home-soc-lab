# Evidence Index

The public repository contains the reviewed Wazuh evidence listed below.
Additional local-only screenshots remain excluded until identifiers are
redacted and the events are verified manager-side.

| File | Purpose | Review status |
|---|---|---|
| `01-wazuh-services-and-api.png` | Manager, indexer, and dashboard active; unauthenticated API request reaches the service and returns the expected HTTP 401 challenge | Published |
| `02-active-agent.png` | `WIN-ENDPOINT-01` active in Wazuh | Published |
| `03-fim-overview.png` | Current FIM added/modified/deleted overview | Published |
| `04-fim-filter-context.png` | FIM dashboard filters and current time window | Published |
| `05-fim-rule-details.png` | Rules 554, 550, and 553 with event types | Published |
| `08-auth-001-wazuh-verification.png` | Event ID 4625 query with three matching Wazuh alerts, including the latest controlled test | Published |
| `06-failed-logon-4625-clean.png` | Controlled Windows 4625 event | Local only; redact identifiers |
| `07-powershell-4104-marked.png` | Controlled PowerShell 4104 marker | Local only; redact identifiers |

## Evidence boundaries

FIM and failed-logon manager-side evidence is verified. The PowerShell image
proves endpoint telemetry; manager-side verification remains pending until that
event is confirmed in the Wazuh dashboard or manager alerts.

## Publication set

The active publication set is:

`01-wazuh-services-and-api.png`, `02-active-agent.png`,
`03-fim-overview.png`, `04-fim-filter-context.png`, and
`05-fim-rule-details.png`, and `08-auth-001-wazuh-verification.png`.

Screenshots 06-07 and images in `Screenshots/archive/` are local working
evidence and should not be published unless specifically reviewed and redacted.
