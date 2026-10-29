# Evidence Review Checklist

Use this checklist before adding screenshots or exports to Git.

## Remove or obscure

- Passwords, tokens, recovery keys, and generated installer credentials
- Personal email addresses
- Full user security identifiers (SIDs)
- Public IP addresses
- Unrelated browser tabs, notifications, and personal files
- Machine identifiers that do not support the investigation

## Keep when relevant

- Detection rule ID, severity, and description
- Sanitized agent name
- Event ID and logon type
- File path when it does not reveal personal information
- Timestamp and time zone
- MITRE ATT&CK mapping
- Short explanation of why the evidence matters

## Screenshot quality

- Crop to the relevant panel.
- Use a readable resolution.
- Give each image a descriptive filename.
- Add a caption in the related report.
- Do not rely on a screenshot as the only evidence source.

## Final verification

- Confirm every screenshot supports a claim in the README or report.
- Confirm unfinished tests are labelled pending.
- Review the staged Git diff before committing.