# Splunk installation and access

Recorded installation: Splunk Enterprise `10.6.1.1` in Ubuntu Server, under `/opt/splunk`. Splunk Web listens on port `8000`.

The VM is headless, so Splunk Web was opened in Chrome on Windows using this VirtualBox NAT port-forwarding rule:

| Setting | Value |
|---|---|
| Protocol | TCP |
| Host IP | `127.0.0.1` |
| Host port | `8000` |
| Guest port | `8000` |

Open `http://127.0.0.1:8000` on the Windows host when the VM and Splunk are running.

Do not publish the Splunk admin password, tokens, or credentials.
