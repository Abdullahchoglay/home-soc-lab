# Evidence Index

These are working evidence files. Review and sanitize the marked images before
publishing. Raw screenshots remain excluded from Git until reviewed.

| File | Purpose | Review status |
|---|---|---|
| `01-wazuh-services-and-api.png` | Manager, indexer, dashboard active; API responds | Needs minor crop review |
| `active agent.png` | `WIN-ENDPOINT-01` active in Wazuh | Needs rename/crop review |
| `03-fim-overview.png` | Current FIM added/modified/deleted overview | Valid overview |
| `04-fim-filter-context.png` | FIM dashboard filters and current time window | Valid context |
| `05-fim-rule-details.png` | Rules 554, 550, and 553 with event types | Valid technical evidence |
| `06-failed-logon-4625-clean.png` | Controlled Windows 4625 event | Must crop identifiers |
| `07-powershell-4104-marked.png` | Controlled PowerShell 4104 marker | Must crop identifiers |
| `VM-config.png` | VirtualBox configuration | Review for machine IDs/paths |
| `ports listening.png` | Wazuh listening ports | Review for local addresses |

## Evidence boundaries

FIM manager-side evidence is verified. The failed-logon and PowerShell images
prove endpoint telemetry; manager-side verification remains pending until those
events are confirmed in the Wazuh dashboard or manager alerts.

## Publication set

The active publication set is the numbered evidence in `Screenshots/`:

`01-wazuh-services-and-api.png`, `02-active-agent.png`,
`03-fim-overview.png`, `04-fim-filter-context.png`,
`05-fim-rule-details.png`, `06-failed-logon-4625-clean.png`, and
`07-powershell-4104-marked.png`.

Images in `Screenshots/archive/` are supplementary historical evidence and
should not be published unless specifically reviewed.