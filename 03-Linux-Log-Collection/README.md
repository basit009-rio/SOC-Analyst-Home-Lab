# Linux authentication log collection

The Ubuntu SSH authentication source reviewed in Splunk was `/var/log/auth.log`.

```spl
index=main source="/var/log/auth.log" sshd
| table _time host source _raw
| sort - _time
```

```spl
index=main source="/var/log/auth.log" "Failed password"
| table _time host _raw
| sort - _time
```

Observed test records included `Invalid user fakeuser` and `Failed password for invalid user fakeuser` from `127.0.0.1`. This confirmed that the SSH activity was logged and searchable.
