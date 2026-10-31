# Lab architecture

```text
Windows 11 host
  └─ Oracle VirtualBox
       └─ Ubuntu Server VM: SOC-Lab-Ubuntu (hostname: soc-lab)
            ├─ SSH authentication activity
            ├─ /var/log/auth.log
            └─ Splunk Enterprise 10.6.1.1
                  └─ SPL searches and scheduled alert
```

Chrome on Windows accesses Splunk Web through VirtualBox NAT port forwarding: host `127.0.0.1:8000` to guest port `8000`. The documented SSH simulation used the local source `127.0.0.1`.
