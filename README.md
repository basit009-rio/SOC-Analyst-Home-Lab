# SOC Analyst Home Lab

Hands-on SOC portfolio lab using Ubuntu Server, Splunk Enterprise, Linux authentication logs, SSH failed-login simulation, SPL detections, and scheduled alerting.

**Status:** Initial documentation of completed exercises; the lab is ongoing.

## Environment

| Component | Details |
|---|---|
| Host | Windows 11 |
| Virtualization | Oracle VirtualBox |
| Guest | Ubuntu Server, headless |
| VM / hostname | `SOC-Lab-Ubuntu` / `soc-lab` |
| SIEM | Splunk Enterprise 10.6.1.1 |
| Log source | `/var/log/auth.log` |
| Splunk Web | `http://127.0.0.1:8000` from Windows via VirtualBox NAT port forwarding |

## Completed work

- Installed Ubuntu Server in VirtualBox and installed Splunk Enterprise.
- Accessed Splunk Web from the Windows host using NAT port forwarding.
- Searched Linux SSH authentication events in `/var/log/auth.log`.
- Generated controlled failed SSH login attempts against the invalid test username `fakeuser`.
- Used SPL `rex`, `bin`, `stats`, and `where` to detect at least three failed logins for the same source IP and username in a five-minute bucket.
- Configured a scheduled alert named **SOC - SSH Brute Force Detection**.
- Reviewed alert history and the underlying SSH events.

## Repository contents

- `01-Lab-Architecture/` — components and data flow.
- `02-Splunk-Installation/` — installation and access notes.
- `03-Linux-Log-Collection/` — authentication log searches.
- `04-SSH-Brute-Force-Detection/` — detection explanation.
- `05-SPL-Queries/` — reusable SPL searches.
- `06-SOC-Investigation-Reports/` — investigation report.
- `07-Alerts/` — alert settings.
- `09-Lessons-Learned/` — troubleshooting notes.

## Key detection

See [`05-SPL-Queries/ssh_brute_force_detection.spl`](05-SPL-Queries/ssh_brute_force_detection.spl).

## Findings and limitations

The documented test activity came from `127.0.0.1` (the local loopback address), not an external attacker. The observed evidence shows failed authentication attempts; it does not prove successful access or compromise. A successful-login investigation and additional telemetry are future improvements.

## Safety

All tests described here were performed in the user's own lab against a test account. Do not test systems without explicit authorization. Never commit passwords, tokens, private keys, or unredacted sensitive screenshots.

## Next improvements

- Add sanitized Splunk screenshots and an architecture diagram.
- Investigate successful SSH logins and correlate them with preceding failures.
- Build dashboards and add further Linux/Windows detections.
- Document additional incident response exercises.

**Author:** Basit Shafi
