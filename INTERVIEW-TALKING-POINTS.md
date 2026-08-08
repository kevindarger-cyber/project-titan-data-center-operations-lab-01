# Interview Talking Points

## 30-Second Summary
I built a Linux server break/fix lab focused on data-center operations. I worked four controlled incidents covering network connectivity, Docker/Nginx application availability, storage-capacity pressure, and high CPU utilization. For each incident I established a healthy baseline, reproduced the fault, isolated the cause, remediated it, and validated recovery instead of assuming the fix worked.

## Strong Examples

### Network Incident
I diagnosed a Linux server that lost external connectivity. I confirmed the outage, compared the routing table to a known-good baseline, identified the primary interface in a DOWN state, restored it, and validated the interface, default route, gateway, external IP connectivity, and DNS.

### Application Incident
I troubleshot a web application outage while the host itself remained reachable. I verified the network first, checked Docker, found the Nginx `homepage` container in an exited state, restarted it, confirmed the port mapping returned, and validated HTTP service with `curl`.

### Storage Incident
I investigated a filesystem that jumped from 1% to 89% utilization. I used `df` to confirm the capacity issue and `du` to identify an 801 MB file consuming the volume. After verifying it was lab test data, I removed it and confirmed utilization returned to 1%.

### CPU Incident
I used `top` to identify a runaway process consuming roughly 95–100% of one CPU core. I terminated the offending PID gracefully and confirmed the process disappeared and CPU idle returned to approximately 99%.

## Key Lesson
I learned to separate symptoms from root causes. A closed port can be a symptom of a stopped application, a missing route can be a symptom of a down interface, and high disk utilization requires identifying what is consuming the space before deleting anything.
