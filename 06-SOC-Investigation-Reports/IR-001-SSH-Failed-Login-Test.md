# IR-001: Repeated SSH failed-login test

| Field | Value |
|---|---|
| Activity | Controlled SSH failed-login simulation |
| Source | Ubuntu `/var/log/auth.log` |
| SIEM | Splunk Enterprise |
| Test username | `fakeuser` |
| Source address | `127.0.0.1` |
| Result | Detection condition met in the lab |

## Summary
A controlled authentication test generated repeated failed SSH password attempts for invalid username `fakeuser`. The events were visible in `/var/log/auth.log` and searchable in Splunk.

## Evidence
Reviewed records included `Invalid user`, `Failed password for invalid user`, and `Connection closed by invalid user` messages. Three failed-password events were visible within a short interval from `127.0.0.1`.

## Assessment
This was an authorized local test. `127.0.0.1` is the loopback address, not a remote attacker IP. The evidence shows failed authentication only; it does not establish successful access or compromise.

## Triage steps
1. Confirm whether the source and test activity are expected.
2. Review surrounding authentication events for the same username and source.
3. Check whether a successful SSH authentication followed the failures.
4. Validate whether the username is legitimate.
5. In a real environment, follow the organization's escalation and account-protection procedures.

## Outcome
The lab demonstrated Linux authentication log visibility, SPL extraction and aggregation, and scheduled alerting. Add sanitized screenshots when available.
