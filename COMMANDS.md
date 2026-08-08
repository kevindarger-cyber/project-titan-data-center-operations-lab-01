# Command Reference

## Network
```bash
ip addr
ip addr show enp0s3
ip route
ping -c 4 10.0.2.2
ping -c 4 8.8.8.8
ping -c 4 google.com
sudo ip link set enp0s3 down
sudo ip link set enp0s3 up
```

## Docker / Web Service
```bash
sudo docker ps
sudo docker ps -a
sudo docker stop homepage
sudo docker start homepage
curl http://localhost:8080
```

## Storage
```bash
df -h
df -h /mnt/dc-storage
sudo fallocate -l 1G /tmp/dc-storage.img
sudo mkfs.ext4 /tmp/dc-storage.img
sudo mkdir -p /mnt/dc-storage
sudo mount -o loop /tmp/dc-storage.img /mnt/dc-storage
sudo fallocate -l 800M /mnt/dc-storage/test-data.bin
sudo du -sh /mnt/dc-storage
sudo du -sh /mnt/dc-storage/*
sudo rm /mnt/dc-storage/test-data.bin
```

## CPU / Processes
```bash
top
yes > /dev/null &
kill 5090
```

> PID values are session-specific. Always identify the current PID before terminating a process.
