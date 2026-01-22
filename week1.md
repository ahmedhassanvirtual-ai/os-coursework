# Week 1: System Planning and Distribution Selection

[← Back to Home](README.md)

## Overview

This week focuses on planning the operating system deployment and making justified technical decisions.

---

## 1. System Architecture Diagram

*Architecture diagram will be added here showing:*
- Server VM (Ubuntu Server - Headless)
- Workstation (Host machine with SSH client)
- Network connections (VirtualBox Host-Only Network)

---

## 2. Distribution Selection Justification

### Chosen Distribution: Ubuntu Server 24.04 LTS

| Criteria | Ubuntu Server | Alternative (Debian) | Alternative (CentOS Stream) |
|----------|---------------|---------------------|----------------------------|
| Documentation | Excellent | Good | Good |
| Community Support | Very Large | Large | Medium |
| Security Updates | 5 years LTS | 5 years | Rolling |
| Package Manager | APT | APT | DNF |
| Beginner Friendly | Yes | Moderate | No |

**Justification:** I chose Ubuntu Server 24.04 LTS because...
- *[To be completed after installation]*

---

## 3. Workstation Configuration Decision

**Chosen Option:** Option B - Host machine with SSH client

**Justification:**
- *[To be completed]*

---

## 4. Network Configuration Documentation

### VirtualBox Network Settings

| Setting | Value |
|---------|-------|
| Adapter Type | Host-Only |
| IP Address (Server) | *[To be added]* |
| IP Address (Workstation) | *[To be added]* |
| Subnet Mask | 255.255.255.0 |

---

## 5. System Specifications (CLI Evidence)

### Command: uname -a
```
[Screenshot will be added here]
```

### Command: free -h
```
[Screenshot will be added here]
```

### Command: df -h
```
[Screenshot will be added here]
```

### Command: ip addr
```
[Screenshot will be added here]
```

### Command: lsb_release -a
```
[Screenshot will be added here]
```

---

## Reflection

*[What I learned this week, challenges faced, and how I resolved them]*

---

## References

*[Any references used this week in IEEE format]*

---

[← Back to Home](README.md) | [Next: Week 2 →](week2.md)
