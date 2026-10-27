# Week 1 evidence checklist

Checked October 27, 2026 for Sujal K Rao, B084D.

| Requirement | Evidence | Status |
| --- | --- | --- |
| VirtualBox and Kali | [VM settings](../evidence/virtualbox-settings.txt), [guest checks](../evidence/guest-verification.txt) | Verified |
| NAT Network 10.0.0.0/24 | [Current screenshot](../screenshots/nat-network.png), [network output](../evidence/nat-network.txt) | Verified |
| VM attached to NAT Network | [VM settings](../evidence/virtualbox-settings.txt) | Verified |
| Clipboard and drag/drop enabled | [VM settings](../evidence/virtualbox-settings.txt) | Both bidirectional; transfers untested |
| Host Downloads shared | [Guest mount](../evidence/guest-verification.txt), [access checks](../evidence/shared-folder-verification.txt) | Mounted; read/traverse checked; no file transfer |
| Manual IP 10.0.0.2/24 | [Guest checks](../evidence/guest-verification.txt) | Verified |
| Internet and DNS | [Guest checks](../evidence/guest-verification.txt) | Gateway/external ping, DNS and HTTPS passed |
| VM snapshot | [Snapshot listing](../evidence/snapshot.txt) | Exists; restore untested |
| Troubleshooting | [Historical image](../screenshots/historical-kali-network-errors.jpeg), [notes](troubleshooting.md) | Historical failures and current recovery documented |

The current settings screenshot is from this computer. The historical error screenshot was supplied by the user. All other evidence consists of real command output, not screenshot images. Instructor example screenshots have not been copied into this submission. VirtualBox's settings dialog became unresponsive during additional screenshot collection; successful command evidence is retained rather than inventing screenshots.

Publishing and the submission form are tracked separately from this lab evidence. This checklist does not claim that the program has graded or accepted the work.

