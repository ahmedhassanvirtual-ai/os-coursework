# Week 5: Advanced Security and Monitoring Infrastructure

**Student:** Ahmed Hassan | **Student ID:** A00022015 | **Module:** CMPN202 Operating Systems

---

## 1. AppArmor Access Control

### AppArmor Status
![AppArmor Status](images/01-apparmor-status.png)

---

### AppArmor Profiles
![AppArmor Profiles](images/02-apparmor-profiles.png)

---

### Install AppArmor Utilities
```bash
sudo apt install apparmor-utils -y
```
![AppArmor Utils](images/03-apparmor-utils-install.png)

---

## 2. Automatic Security Updates

### Install Unattended Upgrades
```bash
sudo apt install unattended-upgrades -y
```
![Install Unattended Upgrades](images/04-install-unattended-upgrades.png)

---

### Enable Automatic Updates
```bash
sudo dpkg-reconfigure unattended-upgrades --priority=low
```
![Enable Auto Updates](images/05-enable-auto-updates.png)

---

### Verify Configuration
![Auto Upgrades Config](images/06-auto-upgrades-config.png)

---

## 3. fail2ban Intrusion Detection

### Install fail2ban
```bash
sudo apt install fail2ban -y
```
![Install fail2ban](images/07-install-fail2ban.png)

---

### Enable fail2ban
```bash
sudo systemctl start fail2ban
sudo systemctl enable fail2ban
```
![Enable fail2ban](images/08-enable-fail2ban.png)

---

### fail2ban Status
![fail2ban Status](images/09-fail2ban-status.png)

---

### SSH Jail Status
![fail2ban SSHD](images/10-fail2ban-sshd.png)

---

## 4. Security Baseline Script (security-baseline.sh)

### Script Code
```bash
#!/bin/bash
# security-baseline.sh
# Purpose: Verify all security configurations from Weeks 4 and 5
# Author: Ahmed Hassan (A00022015)

echo "=========================================="
echo "  Security Baseline Verification Script"
echo "=========================================="

# Check SSH Configuration
echo "[1] Checking SSH Configuration..."
ROOT_LOGIN=$(grep "^PermitRootLogin" /etc/ssh/sshd_config)
PASS_AUTH=$(grep "^PasswordAuthentication" /etc/ssh/sshd_config)
PUBKEY=$(grep "^PubkeyAuthentication" /etc/ssh/sshd_config)

# Check Firewall Status
echo "[2] Checking Firewall Status..."
sudo ufw status verbose

# Check AppArmor Status
echo "[3] Checking AppArmor Status..."
sudo aa-status | head -10

# Check fail2ban Status
echo "[4] Checking fail2ban Status..."
sudo fail2ban-client status

# Check Automatic Updates
echo "[5] Checking Automatic Updates..."
cat /etc/apt/apt.conf.d/20auto-upgrades

# Check Users with Sudo Access
echo "[6] Checking Sudo Users..."
grep -Po '^sudo.+:\K.*$' /etc/group

echo "=========================================="
echo "  Security Baseline Check Complete"
echo "=========================================="
```

![Security Baseline Script](images/11-security-baseline-script.png)

---

### Script Output
![Security Baseline Output](images/12-security-baseline-output.png)

---

## 5. Remote Monitoring Script (monitor-server.sh)

### Script Code
```bash
#!/bin/bash
# monitor-server.sh
# Purpose: Collect performance metrics from the server
# Author: Ahmed Hassan (A00022015)

echo "=========================================="
echo "  Server Monitoring Script"
echo "=========================================="

# CPU Usage
echo "[1] CPU Usage..."
top -bn1 | head -5

# Memory Usage
echo "[2] Memory Usage..."
free -h

# Disk Usage
echo "[3] Disk Usage..."
df -h | grep -E "^/dev"

# Network Connections
echo "[4] Network Connections..."
ss -tuln | head -10

# System Uptime and Load
echo "[5] System Load..."
uptime

# Running Services
echo "[6] Running Services..."
systemctl list-units --type=service --state=running | head -10

echo "=========================================="
echo "  Monitoring Complete"
echo "=========================================="
```

![Monitor Script](images/13-monitor-script.png)

---

### Script Output
![Monitor Output](images/14-monitor-output.png)

---

## 6. Security Summary

| Security Control | Status |
|-----------------|--------|
| AppArmor | ✅ Active |
| Automatic Updates | ✅ Enabled |
| fail2ban | ✅ Running |
| security-baseline.sh | ✅ Created |
| monitor-server.sh | ✅ Created |

---

## 7. Reflection

**Learned:** AppArmor configuration, automatic updates setup, fail2ban intrusion detection, bash scripting with comments.

**Scripts Created:** Two scripts for security verification and performance monitoring, both with line-by-line comments.

---

*Week 5 Complete - Ahmed Hassan (A00022015)*