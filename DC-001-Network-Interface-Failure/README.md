# DC-001 — Network Interface Failure

## Scenario
`titan-ubuntu` lost external network connectivity.

## Baseline
- Primary interface `enp0s3` was UP with IPv4 `10.0.2.15/24`.
- Default route used gateway `10.0.2.2`.
- Gateway, external IP, and DNS tests succeeded.

## Failure
The primary interface was intentionally placed in a DOWN state to simulate loss of network connectivity.

## Investigation
1. Verified external connectivity failed with `Network is unreachable`.
2. Checked `ip route` and observed the default route and `10.0.2.0/24` route were missing.
3. Checked `ip addr` and found `enp0s3` in `state DOWN`.

## Root Cause
The primary network interface `enp0s3` was administratively down. This removed the interface's active IPv4 configuration and associated default route. No physical NIC failure was established.

## Remediation
```bash
sudo ip link set enp0s3 up
```

## Validation
- `enp0s3` returned to `UP,LOWER_UP`.
- IPv4 `10.0.2.15/24` returned.
- Default route through `10.0.2.2` returned.
- Gateway ping: 0% packet loss.
- External IP ping: 0% packet loss.
- DNS/hostname ping: 0% packet loss.

## Evidence
See the [`evidence`](./evidence/) folder for all 15 screenshots.
