# Week 1 verification evidence

Collected from the existing VirtualBox VM on 27 October 2026 at approximately 05:01–05:03 UTC. These are real command outputs, not screenshots or reconstructed terminal images.

## Verified

- VirtualBox version: 7.2.22r175245.
- Existing VM: `kali-linux-2026.3-virtualbox-amd64`, Kali Rolling 2026.3.
- VM adapter attached to `NatNetwork`; network `10.0.0.0/24`, gateway `10.0.0.1`.
- Guest `eth0` is UP with `10.0.0.2/24`; the active NetworkManager profile uses `ipv4.method=manual`.
- Default route uses `10.0.0.1`; configured DNS is `8.8.8.8`; `ipv4.dad-timeout` is `0`.
- Gateway and external IP connectivity: each ping received 3 of 3 replies, with 0% packet loss.
- DNS resolved `example.com`; an HTTPS HEAD request to that site returned HTTP/2 200.
- Host Downloads share is mounted as `vboxsf` at `/media/sf_Downloads`. Guest read and traverse checks passed. Write permission exists, but no file was written during verification.
- Shared Clipboard and Drag and Drop are configured as bidirectional.
- Existing current snapshot is named `Kali - Network Working`.
- Nmap is installed, version 7.991. No scanning was performed.

## Evidence files

- `virtualbox-settings.txt`: filtered direct VM configuration output.
- `nat-network.txt`: direct NAT network configuration output.
- `guest-verification.txt`: live OS, IP, route, NetworkManager, share mount, ping, DNS and HTTPS checks.
- `shared-folder-verification.txt`: live permission checks without accessing personal file contents.
- `nmap-version.txt`: version output only.
- `snapshot.txt`: existing snapshot listing.

## Limits

Clipboard copy/paste and drag/drop transfers were not exercised. Their settings were verified only. No shared-folder file transfer was performed. The snapshot was not restored or tested. No configuration changes were made. The VM was started for the live checks and left running for screenshot collection.

The earlier user-supplied screenshot records failed commands before the user reported fixing Kali. It must be labelled historical troubleshooting evidence and does not prove the successful checks above.
