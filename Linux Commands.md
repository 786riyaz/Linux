Below is a **complete, structured command reference** specifically for **Raspberry Pi 3 running Raspberry Pi OS**, covering **RAM, CPU, storage, OS, kernel, temperature, hardware, network, and performance**.
All commands are **safe**, **read-only**, and suitable for production diagnostics.

---

# Raspberry Pi 3 – Complete System Information Commands

---

## 1️⃣ RAM & MEMORY DETAILS (Most Important)

### 1. Total, Used, Free RAM

```bash
free -h
```

**Use:** Daily memory check
**Key field:** `available`

---

### 2. Detailed Memory Statistics

```bash
cat /proc/meminfo
```

**Use:** Kernel-level memory info

---

### 3. Only Total Installed RAM

```bash
grep MemTotal /proc/meminfo
```

---

### 4. Real-Time Memory Usage (Interactive)

```bash
htop
```

If not installed:

```bash
sudo apt install htop
```

---

### 5. Memory Usage per Process

```bash
ps aux --sort=-%mem | head
```

---

## 2️⃣ CPU DETAILS

### 6. CPU Model & Core Info

```bash
lscpu
```

---

### 7. CPU Temperature

```bash
vcgencmd measure_temp
```

---

### 8. CPU Frequency (Live)

```bash
vcgencmd measure_clock arm
```

---

### 9. CPU Throttling / Undervoltage Check

```bash
vcgencmd get_throttled
```

| Value    | Meaning                 |
| -------- | ----------------------- |
| `0x0`    | No issues               |
| Non-zero | Power / thermal problem |

---

## 3️⃣ DISK & STORAGE

### 10. Disk Usage (Human Readable)

```bash
df -h
```

---

### 11. Folder Size (Find Space Hogs)

```bash
du -sh /*
```

---

### 12. SD Card & Partitions

```bash
lsblk
```

---

## 4️⃣ OPERATING SYSTEM & KERNEL

### 13. OS Version

```bash
cat /etc/os-release
```

---

### 14. Kernel Version

```bash
uname -a
```

---

### 15. Bootloader & Firmware Version

```bash
vcgencmd version
```

---

## 5️⃣ HARDWARE INFORMATION

### 16. Raspberry Pi Model & Revision

```bash
cat /proc/cpuinfo
```

---

### 17. Device Tree Hardware Info

```bash
vcgencmd get_config int
```

---

### 18. USB Devices

```bash
lsusb
```

---

### 19. Connected PCI Devices (if any)

```bash
lspci
```

---

## 6️⃣ NETWORK INFORMATION

### 20. Network Interfaces

```bash
ip a
```

---

### 21. IP Address Only

```bash
hostname -I
```

---

### 22. Wi-Fi Details

```bash
iwconfig
```

---

### 23. Internet Connectivity Test

```bash
ping -c 4 google.com
```

---

## 7️⃣ PERFORMANCE & LOAD

### 24. System Load Average

```bash
uptime
```

---

### 25. Detailed Performance Stats

```bash
vmstat 1
```

---

### 26. Running Services

```bash
systemctl list-units --type=service --state=running
```

---

## 8️⃣ POWER & THERMAL STATUS (Very Important for Pi 3)

### 27. Voltage Status

```bash
vcgencmd measure_volts
```

---

### 28. Throttling History

```bash
vcgencmd get_throttled
```

---

## 9️⃣ BOOT & STARTUP ANALYSIS

### 29. Boot Time Analysis

```bash
systemd-analyze
```

---

### 30. Slow Boot Services

```bash
systemd-analyze blame
```

---

## 🔟 LOGS & ERRORS

### 31. System Logs

```bash
journalctl -xe
```

---

### 32. Kernel Logs

```bash
dmesg | tail
```

---

## 1️⃣1️⃣ GPIO & PI-SPECIFIC

### 33. GPIO Pin Status

```bash
raspi-gpio get
```

---

### 34. Raspberry Pi Configuration

```bash
sudo raspi-config
```

---

## 📌 ONE-SHOT FULL SYSTEM REPORT (Recommended)

Install:

```bash
sudo apt install neofetch
```

Run:

```bash
neofetch
```

Displays:

* OS
* Kernel
* RAM
* CPU
* GPU
* Uptime
* Resolution

---

## ✅ BEST COMMANDS SUMMARY (Quick Use)

| Purpose      | Command                  |
| ------------ | ------------------------ |
| RAM usage    | `free -h`                |
| Live monitor | `htop`                   |
| CPU temp     | `vcgencmd measure_temp`  |
| Disk space   | `df -h`                  |
| OS info      | `cat /etc/os-release`    |
| Hardware     | `cat /proc/cpuinfo`      |
| Network      | `ip a`                   |
| Power issues | `vcgencmd get_throttled` |

---

## ⚠️ Important Notes for Raspberry Pi 3

* Total RAM ≈ **1 GB**
* Avoid heavy desktop apps
* Enable swap only if required
* Use **official 5V 2.5A power supply**
* Overheating causes throttling

---

If you want, I can:

* Convert this into a **single text file**
* Create a **shell script** that exports all info into one report
* Help optimize RAM usage for your specific workload

Just tell me your preference.
