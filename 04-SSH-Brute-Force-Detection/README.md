# SSH brute-force detection

## Objective
Detect at least three failed SSH password attempts for the same source IP and target username within a five-minute time bucket.

## Controlled test
Repeated failed SSH password attempts were generated against invalid test username `fakeuser` from local host `127.0.0.1`. The reviewed SSH daemon records included invalid-user, failed-password, and connection-closed messages. Three failed-password events were visible within a short interval.

This is a local lab simulation, not evidence of an external attack or confirmed compromise.

Detection SPL: [`../05-SPL-Queries/ssh_brute_force_detection.spl`](../05-SPL-Queries/ssh_brute_force_detection.spl).
