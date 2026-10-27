# Kali network troubleshooting

## Observed problem

The [historical terminal screenshot](../screenshots/historical-kali-network-errors.jpeg) records three failed attempts during network configuration:

| Observation | What it establishes | Corrective guidance |
| --- | --- | --- |
| `sudo mcli ...` returned `command not found` | The command name was mistyped. | Use `nmcli`, the NetworkManager command-line tool. |
| `nmcli connection up "Wired connection 1"` returned an IP configuration activation error | The connection did not activate at that attempt. | Check the active profile, NAT attachment, address settings, and possible duplicate addresses; the message alone does not establish the cause. |
| A modification command contained `ipv4. gateway` and returned an invalid-property error | A space split the property name. | Use `ipv4.gateway` as one token. |

## Recovery status

Kali was subsequently fixed. Live verification on October 27, 2026 now confirms manual `10.0.0.2/24` addressing, the expected gateway and DNS, successful gateway and external-IP pings, DNS resolution, and an HTTPS HTTP/2 200 response. See the [actual guest output](../evidence/guest-verification.txt).

The active profile has `ipv4.dad-timeout=0`, matching the guide's workaround. The historical screenshot does not show the successful repair sequence, so the evidence establishes current recovery without proving which change caused it.

## Correct syntax reference

For a profile actually named `Wired connection 1`, the guide's intended static settings can be expressed as:

```sh
sudo nmcli connection modify "Wired connection 1" \
  ipv4.method manual \
  ipv4.addresses 10.0.0.2/24 \
  ipv4.gateway 10.0.0.1 \
  ipv4.dns 8.8.8.8
```

This is a syntax reference, not a record that this exact command was successfully run. Confirm the actual connection name before applying commands. The guide also suggests DNS `10.0.0.1` if the illustrated DNS setting causes internet issues.

## Guide's additional remedy

Page 7 suggests the following for certain VirtualBox/Kali connectivity issues after checking NAT configuration and duplicate IP addresses:

```sh
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

The guide then advises restarting Kali. These are the instructor's recommendations. The current timeout setting is verified as `0`, but the exact sequence of earlier changes and its causal effect are not established.

## Final verification

Gateway and external-IP pings each returned 3 of 3 replies with 0% loss. DNS resolved `example.com`, and an HTTPS HEAD request returned HTTP/2 200. The Downloads share is mounted and accessible to the guest user. These are current tests; they do not reconstruct the earlier repair steps. No network settings were changed during this verification.

