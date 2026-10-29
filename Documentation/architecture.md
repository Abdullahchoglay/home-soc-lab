# Lab Architecture

## Components

| Component | Platform | Purpose |
|---|---|---|
| Host and endpoint | Windows 11 | Runs VirtualBox and provides endpoint telemetry |
| Wazuh server | Ubuntu Server 24.04 LTS | Manager, indexer, and dashboard |
| Endpoint agent | Wazuh Agent 4.14.7 | Collects Windows security and integrity events |
| Virtualization | VirtualBox | Hosts the Ubuntu SOC server |

## Data Flow

```text
WIN-ENDPOINT-01
    |
    | Secure event transport (TCP 1514)
    | Agent enrollment (TCP 1515)
    v
VirtualBox localhost NAT forwarding
    |
    v
Ubuntu Wazuh manager -> Wazuh indexer -> Wazuh dashboard
```

The VirtualBox rules bind only to `127.0.0.1`, so the forwarded services are
not intentionally exposed to other devices on the local network.

## Telemetry

- Windows Application, Security, and System event logs
- Windows PowerShell Operational log
- Wazuh File Integrity Monitoring
- Wazuh system inventory

## Current Limitations

- Sysmon is not installed yet.
- A VM snapshot is deferred because the Windows C: drive has limited free space.
- Five reviewed screenshots are published; Windows event screenshots containing
  local identifiers remain excluded.
