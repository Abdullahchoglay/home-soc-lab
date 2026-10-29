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

Guest Control initially became unreliable while the VM and Wazuh agent kept
running. After service recovery, AUTH-001 was verified in Wazuh Discover. For
PS-001, the custom rule was installed, syntax-checked, and verified directly
with `wazuh-logtest`. Live Rule 100101 indexing is not claimed by the published
scope.

**Lesson:** record the exact validation boundary and never present an unverified
result as complete.

## Wazuh dashboard query input through VirtualBox

Mouse input worked in the dashboard, but synthetic keyboard input was rejected
by the VirtualBox console during the final PS-001 query. Manager logs were
checked directly and the rule was tested with Wazuh's native rule-test utility.

**Lesson:** use independent validation paths and retain text evidence when a UI
capture path is unreliable.
