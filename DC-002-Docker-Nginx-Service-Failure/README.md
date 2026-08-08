# DC-002 — Docker / Nginx Service Failure

## Scenario
`titan-ubuntu` remained reachable, but the Nginx web application on TCP/8080 was unavailable.

## Baseline
- External network connectivity was healthy.
- Docker container `homepage` was running.
- Host port `8080` mapped to container port `80`.
- `curl http://localhost:8080` returned the Project Titan HTML page.

## Investigation
1. Verified network connectivity remained healthy.
2. `sudo docker ps` showed no running containers.
3. `sudo docker ps -a` showed `homepage` in `Exited (0)` state.

## Root Cause
The `homepage` Nginx container had been stopped, making its published TCP/8080 service unavailable.

## Remediation
```bash
sudo docker start homepage
```

## Validation
- `sudo docker ps` showed `homepage` in an `Up` state.
- Port mapping `8080->80/tcp` was restored.
- `curl http://localhost:8080` successfully returned application HTML.

## Evidence
See the [`evidence`](./evidence/) folder for all 10 screenshots.
