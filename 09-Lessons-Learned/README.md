# Lessons learned and troubleshooting

## Skills practiced
- Finding SSH authentication activity in `/var/log/auth.log`.
- Extracting fields with SPL `rex`.
- Grouping events with `bin _time span=5m`.
- Counting events with `stats` and applying thresholds with `where`.
- Configuring and validating a scheduled Splunk alert.
- Distinguishing local test activity (`127.0.0.1`) from external traffic.

## Troubleshooting notes

### Splunk Web from Windows
The Ubuntu VM used VirtualBox NAT, so a TCP port-forwarding rule was needed to reach `http://127.0.0.1:8000` from Windows.

### Headless Ubuntu
The VM has no desktop environment. Use the Windows host browser for Splunk Web.

### Minimum free disk space warning
Splunk displayed a warning that its minimum free disk space threshold (5000 MB) had been reached for its dispatch area. The root filesystem was close to that threshold. Check disk space before troubleshooting SPL:

```bash
df -h /
```

Do not delete Splunk index files or system files blindly.

### Search mode
Fast Mode may not display raw events. Use Verbose Mode when inspecting event details during an investigation.
