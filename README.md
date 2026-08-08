# Project Titan: Data Center Operations Lab — Lab 01 Server Break/Fix

## Overview
This lab documents four controlled break/fix incidents performed in an Ubuntu Linux virtualized environment. The goal was to practice a repeatable data-center troubleshooting workflow: establish a baseline, verify the incident, isolate the fault domain, remediate the issue, validate recovery, and document the outcome.

> **Lab type:** Home lab / simulated production incidents  
> **Platform:** Ubuntu Linux on Oracle VirtualBox  
> **Technologies:** Linux networking, Docker, Nginx, ext4, loop devices, process monitoring, TCP/IP, DNS  
> **Methodology:** Baseline → Verify → Investigate → Isolate → Diagnose → Remediate → Validate → Document

## Incidents

### DC-001 — Network Interface Failure
Simulated loss of external connectivity by taking the primary network interface offline. Investigated interface state and routing, restored the interface, and validated gateway, internet, and DNS connectivity.

[View DC-001](./DC-001-Network-Interface-Failure/README.md)

### DC-002 — Docker / Nginx Service Failure
Simulated a web-service outage while the Linux host remained network-accessible. Distinguished host-network health from application health, identified a stopped Nginx container, restored it, and validated HTTP service on TCP/8080.

[View DC-002](./DC-002-Docker-Nginx-Service-Failure/README.md)

### DC-003 — Storage Capacity Incident
Built a safe 1 GB ext4 test filesystem, simulated storage pressure to 89% utilization, identified the space-consuming file, removed verified test data, and validated recovery to 1% utilization.

[View DC-003](./DC-003-Storage-Capacity-Incident/README.md)

### DC-004 — CPU Resource Incident
Created a controlled runaway CPU process, identified the offending PID with `top`, terminated it gracefully, and validated return to approximately 99% CPU idle.

[View DC-004](./DC-004-CPU-Resource-Incident/README.md)

## Skills Demonstrated
- Linux network interface and routing troubleshooting
- Gateway, external IP, and DNS validation
- Docker container lifecycle troubleshooting
- Nginx/HTTP service validation with `curl`
- Filesystem capacity analysis with `df` and `du`
- ext4 filesystem creation and loop-device mounting
- Linux process and CPU analysis with `top`
- PID-based process remediation with `kill`
- Incident documentation and validation discipline
- Layered troubleshooting across network, application, storage, and compute resources

## Important Note
All faults in this project were intentionally created in a controlled home-lab environment. The project demonstrates troubleshooting methodology and technical practice; it does not represent production data-center employment experience.

## Repository Structure
```text
Project-Titan-Data-Center-Operations-Lab-01/
├── README.md
├── COMMANDS.md
├── INTERVIEW-TALKING-POINTS.md
├── RESUME-BULLETS.md
├── DC-001-Network-Interface-Failure/
├── DC-002-Docker-Nginx-Service-Failure/
├── DC-003-Storage-Capacity-Incident/
└── DC-004-CPU-Resource-Incident/
```
