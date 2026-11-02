# Splunk Lab Health Check

## 1. Objective
Verify the successful startup and operational status of Splunk Enterprise in the SOC home lab.

## 2. Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Host OS | Windows 11 |
| Server OS | Ubuntu Server |
| SIEM | Splunk Enterprise 10.6.1.1 |
| Installation Path | /opt/splunk |
| Service Account | splunk |

## 3. Troubleshooting and Diagnosis

Initially, Splunk was not running.

The following checks were performed:

**Check installation directory ownership**

```bash
ls -ld /opt/splunk
```

Result: Directory owned by user `splunk` and group `splunk`.

**Verify Splunk service account**

```bash
getent passwd splunk
```

Result: Splunk service account successfully verified.

## 4. Starting Splunk

Command executed:

```bash
sudo -u splunk /opt/splunk/bin/splunk start
```

## 5. Startup Verification Results

- All preliminary checks passed.
- Configuration validation completed.
- Installed files integrity verified.
- Splunk daemon (splunkd) started successfully.
- HTTP port 8000 available.
- Management port 8089 available.
- Splunk Web successfully started.

## 6. Important Technical Knowledge

- Linux service account management.
- Linux directory ownership and permissions.
- Principle of Least Privilege.
- Splunk service management.
- Splunk network ports.

## 7. Splunk Network Ports

| Port | Purpose |
|---|---|
| 8000 | Splunk Web Interface |
| 8089 | Splunk Management API |
| 9997 | Splunk Forwarder Receiving Port |

## 8. Conclusion

Successfully started Splunk Enterprise 10.6.1.1 using its dedicated Linux service account.

The SOC home lab is ready for further SIEM configuration, log collection and security investigations.

## 9. Evidence

Screenshots of the successful startup and service account verification will be uploaded to this repository.
