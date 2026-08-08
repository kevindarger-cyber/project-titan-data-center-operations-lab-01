# DC-003 — Storage Capacity Incident

## Scenario
A test filesystem mounted at `/mnt/dc-storage` generated a high-utilization alert while the server remained operational.

## Lab Setup
A safe 1 GB disk-image-backed ext4 filesystem was created and mounted with a loop device so the exercise would not intentionally fill the Ubuntu root filesystem.

## Baseline
`/mnt/dc-storage` was approximately 1% utilized with about 907 MB available.

## Failure
An 800 MB test file was created inside the test filesystem, increasing utilization to 89%.

## Investigation
1. `df -h /mnt/dc-storage` confirmed 89% utilization with only 107 MB available.
2. `du` confirmed approximately 801 MB was consumed in the mount.
3. `du -sh /mnt/dc-storage/*` identified `test-data.bin` as the primary space consumer.

## Root Cause
A large lab test file (`test-data.bin`) consumed approximately 801 MB of the 974 MB filesystem.

## Remediation
After confirming the file was safe lab data:
```bash
sudo rm /mnt/dc-storage/test-data.bin
```

## Validation
`df -h /mnt/dc-storage` showed utilization returned from 89% to 1%, restoring approximately 907 MB of available capacity.

## Evidence
See the [`evidence`](./evidence/) folder for all 11 screenshots.
