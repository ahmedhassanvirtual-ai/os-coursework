# Week 4: Initial System Configuration & Security Implementation

**Student:** Ahmed Hassan | **Student ID:** A00022015 | **Module:** CMPN202 Operating Systems

---

## 1. SSH Configuration with Key-Based Authentication

### SSH Config (BEFORE)
![SSH Config Before](images/01-ssh-config-before.png)

![SSH Configuration 2](images/01-ssh-configuration-2.png)

---

### Generate SSH Key (Windows)
```powershell
ssh-keygen -t ed25519 -C "ahmed@a00022015"
```
![SSH Keygen](images/04-ssh-keygen.png)

---

### View Public Key
![SSH Public Key](images/05-ssh-public-key.png)

---

### Copy Key to Server
```powershell
ssh-copy-id ahmed@192.168.56.101
```
![SSH Copy ID](images/06-ssh-copy-id.png)

---

### Test Key-Based Login (No Password!)
![SSH Key Login](images/07-ssh-key-login.png)

---

### SSH Config Edit
Added to `/etc/ssh/sshd_config`:
```
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
```
![SSH Config Edit](images/08-ssh-config-edit.png)

---

### SSH Config (AFTER)
![SSH Config After](images/09-ssh-config-after.png)

---

## 2. Firewall Configuration

### Firewall Status (BEFORE)
![Firewall Before](images/02-firewall-before.png)

---

### Configure UFW Rules
```bash
sudo ufw allow from 192.168.56.1 to any port 22
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable
```
![UFW Allow SSH](images/10-ufw-allow-ssh.png)

![UFW Defaults](images/11-ufw-defaults.png)

![UFW Enable](images/12-ufw-enable.png)

---

### Firewall Status (AFTER)
![Firewall After](images/13-firewall-after.png)

### Firewall Rules Summary

| Rule | Action | From |
|------|--------|------|
| Port 22 (SSH) | ALLOW | 192.168.56.1 only |
| All other incoming | DENY | Any |
| Outgoing | ALLOW | Any |

---

## 3. User Privilege Management

### Users (BEFORE)
![Users Before](images/03-users-before.png)

---

### Create Non-Root Admin User
```bash
sudo adduser sysadmin
sudo usermod -aG sudo sysadmin
```
![Create User](images/14-create-user.png)

![Add Sudo](images/15-add-sudo.png)

---

### Users (AFTER)
![Users After](images/16-users-after.png)

---

### Verify Sudo Access
![Verify Sudo](images/17-verify-sudo.png)

---

## 4. Security Summary

| Security Control | Status |
|-----------------|--------|
| SSH Key-Based Auth | ✅ Enabled |
| Password Auth Disabled | ✅ Disabled |
| Root Login Disabled | ✅ Disabled |
| UFW Firewall | ✅ Active |
| SSH Restricted to Workstation | ✅ 192.168.56.1 only |
| Non-Root Admin User | ✅ sysadmin created |

---

## 5. Reflection

**Learned:** SSH hardening, key-based authentication, UFW firewall configuration, user privilege management.

**Challenges:** Had to add settings at end of sshd_config file since defaults were commented.

---

*Week 4 Complete - Ahmed Hassan (A00022015)*
