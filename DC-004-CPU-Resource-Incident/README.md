# DC-004 — CPU Resource Incident

## Scenario
`titan-ubuntu` generated an elevated-CPU alert and appeared slower while remaining online.

## Baseline
`top` showed approximately 92.8% CPU idle with low system load.

## Failure
A controlled CPU-consuming process was created using:
```bash
yes > /dev/null &
```

## Investigation
`top` identified PID `5090` (`yes`) consuming approximately 94.6% CPU on one core. System load average also increased.

## Root Cause
A runaway `yes` process was continuously consuming CPU resources.

## Remediation
The process was terminated gracefully:
```bash
kill 5090
```

## Validation
- PID `5090` no longer appeared in `top`.
- CPU returned to approximately 99% idle.
- Load average remained temporarily elevated because load averages decay over time.

## Evidence
See the [`evidence`](./evidence/) folder for all 5 screenshots.
