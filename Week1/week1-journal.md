# Week 1: System Planning and Distribution Selection

**Student:** Ahmed Hassan | **Student ID:** A00022015 | **Module:** CMPN202 Operating Systems

---

## 1. System Architecture Diagram

![System Architecture Diagram](images/architecture-diagram.svg)

| Component | Details |
|-----------|---------|
| **Server** | Ubuntu Server 24.04.3 LTS (Headless) |
| **Workstation** | Windows Host with SSH (Option B) |
| **Hypervisor** | VirtualBox 7.x |
| **SSH Access** | 192.168.56.101:22 |

---

## 2. Distribution Selection Justification

**Chosen:** Ubuntu Server 24.04.3 LTS

| Criteria | Ubuntu Server | Debian 12 | Rocky Linux 9 |
|----------|---------------|-----------|---------------|
| Support | 5 years LTS | Long-term | 10 years |
| Security | AppArmor | AppArmor | SELinux |
| Documentation | Excellent | Good | Good |

**Why Ubuntu:** LTS support, extensive documentation, AppArmor included, industry-standard for cloud servers.

---

## 3. Workstation Configuration

**Chosen:** Option B - Windows Host with SSH Client

**Reasons:** Resource efficient (one VM), native SSH in PowerShell, simpler setup, mirrors real-world administration.

---

## 4. Network Configuration

### VirtualBox Network Setup
![VirtualBox Network](images/01-virtualbox-network-setup.png)

### Adapter Configuration

| Adapter | Type | Interface | IP Address |
|---------|------|-----------|------------|
| Adapter 1 | NAT | enp0s3 | 10.0.2.15 |
| Adapter 2 | Host-only | enp0s8 | 192.168.56.101 |

### Host-only Adapter
![Host-only Adapter](images/13-adapter2-host-only.png)

### Netplan Configuration
![Netplan Config](images/14-netplan-config.png)

---

## 5. VM Installation Evidence

### VM Creation
![VM Creation](images/02-vm-creation-name.png)

### Network Configuration
![Network Config](images/03-network-config.png)

### Storage Configuration
![Storage Config](images/04-storage-configuration.png)

### Profile Setup
![Password Config](images/05-password-configuration.png)

### Featured Snaps
![Featured Snaps](images/06-featured-snaps.png)

### SSH Server Installation
![OpenSSH](images/06-openssh.png)

### Installation Complete
![Installation Complete](images/07-installation-complete.png)

---

## 6. CLI System Specifications

### First Login
![First Login](images/09-first-login.png)

### Memory and Disk Space (`free -h` and `df -h`)
![Memory and Space](images/10-memory-and-space.png)

### IP Address (`ip addr`)
![IP Address](images/11-ipaddress.png)

### Two Network Adapters Working
![Two Adapters](images/15-ip-addr-two-adapters.png)

### Distribution Info (`cat /etc/os-release`)
![OS Release](images/12-os-release-output.png)

---

## 7. SSH Connection Evidence

![SSH Connection](images/16-ssh-connection-windows.png)

SSH successfully established from Windows PowerShell to Ubuntu Server at 192.168.56.101.

---

## 8. Reflection

**Learned:** VirtualBox networking (NAT vs Host-only), Ubuntu Server installation, netplan configuration, SSH remote access.

**Challenges:** Host-only adapter needed manual netplan configuration to get IP address.

---

*Week 1 Complete - Ahmed Hassan (A00022015)*