# Troubleshooting Record

## Unsupported Ubuntu release

An early VM used a newer Ubuntu release that was not listed as supported for the
Wazuh central components. The VM was rebuilt using Ubuntu Server 24.04 LTS.

**Lesson:** verify platform support before investing time in installation.

## Insufficient VM and host storage

The first VM had insufficient resources, and the Windows host also reached very
low free space. The VM was rebuilt with a larger dynamically allocated disk
after host storage was recovered.

**Lesson:** a dynamically allocated virtual disk still needs real host capacity
as it grows. Monitor both guest and host usage.

## Incorrect VM time

Ubuntu package updates reported that repository release files were not valid
yet. The VM clock was several days behind. Correcting time synchronization fixed
the package-manager errors.

**Lesson:** accurate time is essential for package validation and security-event
correlation.

## Corrupted or incomplete Windows MSI

The initial Wazuh agent MSI could not be opened. A fresh package was downloaded
from the official Wazuh source and its Authenticode signature was validated.

**Lesson:** verify size, download status, signature, and hash before repeatedly
troubleshooting an installer.

## Missing Windows Wazuh service

`WazuhSvc` did not exist because the agent installation had never completed.
After the valid MSI was installed with administrator privileges, the service
appeared and started normally.

**Lesson:** distinguish installation failure from service-start failure.

## VirtualBox NAT reachability

The Ubuntu guest used the common NAT address `10.0.2.15`, which was not directly
reachable from the host for Wazuh enrollment. Localhost NAT forwarding for TCP
1514 and 1515 resolved endpoint-to-manager communication.

**Lesson:** validate the network path before blaming agent configuration.

## VirtualBox Guest Control authentication

Guest Control initially allowed direct verification of Wazuh alerts but later
stopped accepting new Ubuntu sessions. The VM and Wazuh agent continued running.
AUTH-001 and PS-001 were therefore documented as endpoint-verified but pending
manager-side verification.

**Lesson:** record the exact validation boundary and never present an unverified
result as complete.