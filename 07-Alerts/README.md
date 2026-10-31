# Splunk alert configuration

## SOC - SSH Brute Force Detection

| Setting | Value |
|---|---|
| Type | Scheduled |
| Cron | `*/5 * * * *` (every five minutes) |
| Search time range | Last 5 minutes |
| Trigger | Number of results greater than 0 |
| Trigger frequency | Once |

The alert runs the SPL in `05-SPL-Queries/ssh_brute_force_detection.spl`. Its trigger history showed alert executions. A triggered alert means the search returned results; it is not by itself proof of compromise.

For production use, validate time boundaries, scheduling, duplicate notifications, and throttling.
