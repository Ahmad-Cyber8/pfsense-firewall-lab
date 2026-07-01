# 🔥 pfSense Firewall Lab

> pfSense 2.8.1 firewall configuration with WAN/LAN ruleset and traffic filtering on VMware

![pfSense](https://img.shields.io/badge/pfSense-2.8.1-blue?style=flat-square)
![VMware](https://img.shields.io/badge/Platform-VMware-607078?style=flat-square&logo=vmware)
![Kali](https://img.shields.io/badge/Client-Kali%20Linux-557C94?style=flat-square&logo=kalilinux)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

---

## 📌 Overview

This lab demonstrates a fully configured **pfSense 2.8.1 firewall** deployed in a VMware Workstation environment. The lab covers WAN/LAN interface setup, firewall ruleset design, traffic filtering, and security hardening — with a Kali Linux client connected to the LAN interface for testing.

---

## 🎯 Objectives

- Deploy and configure pfSense 2.8.1 on VMware Workstation
- Set up WAN and LAN interfaces with correct addressing
- Design and implement firewall rules for traffic control
- Test and verify rule enforcement using a Kali Linux client
- Understand rule ordering and default deny policies

---

## 🖥️ Lab Environment

| Component | Details |
|-----------|---------|
| Firewall OS | pfSense 2.8.1 |
| Platform | VMware Workstation |
| WAN Interface | External network (NAT) |
| LAN Interface | Internal network (Host-Only) |
| LAN Client | Kali Linux |

---

## 🌐 Network Topology

```
[Internet / WAN]
       │
  ┌────┴────┐
  │ pfSense │  ← Firewall (2.8.1)
  │ 2.8.1   │
  └────┬────┘
       │ LAN
  ┌────┴────┐
  │  Kali   │  ← LAN Client (testing)
  │  Linux  │
  └─────────┘
```

---

## ⚙️ Configuration

### Interface Setup

| Interface | Type | Role |
|-----------|------|------|
| WAN | NAT (VMware) | External connectivity |
| LAN | Host-Only (VMware) | Internal network |

### Firewall Rules Implemented

| Rule # | Direction | Protocol | Source | Destination | Action |
|--------|-----------|----------|--------|-------------|--------|
| 1 | LAN → WAN | TCP | LAN net | Any | Allow (HTTP/HTTPS) |
| 2 | LAN → WAN | ICMP | LAN net | Any | Allow (Ping) |
| 3 | WAN → LAN | Any | Any | LAN net | Block |
| 4 | LAN → WAN | Any | LAN net | Any | Block (Default Deny) |

---

## 🛡️ Key Concepts Demonstrated

- **Rule ordering** — pfSense processes rules top-down; first match wins
- **Default deny** — all unmatched traffic blocked at the bottom
- **WAN blocking** — inbound connections from WAN rejected by default
- **LAN filtering** — only permitted protocols allowed outbound

---

## 🚀 Setup Steps

### 1 — Deploy pfSense on VMware

- Create new VM with 2 network adapters (NAT + Host-Only)
- Boot from pfSense ISO
- Assign WAN = NAT adapter, LAN = Host-Only adapter

### 2 — Initial Configuration

```
WAN IP: assigned via DHCP (NAT)
LAN IP: 192.168.1.1/24 (static)
```

### 3 — Access Web GUI

```
URL: https://192.168.1.1
Default credentials: admin / pfsense
```

### 4 — Configure Firewall Rules

- Navigate to **Firewall** → **Rules**
- Add rules for LAN and WAN interfaces
- Apply and test each rule

---

## 📊 Results

- ✅ pfSense successfully deployed on VMware
- ✅ WAN/LAN interfaces configured correctly
- ✅ Firewall rules enforced — permitted traffic allowed
- ✅ Blocked traffic confirmed via Kali Linux testing
- ✅ Default deny policy working correctly

---

## 📁 Project Structure

```
pfsense-firewall-lab/
├── README.md                     # Project documentation
├── report/
│   └── pfSense_Lab_Report.pdf    # Full lab report
└── screenshots/
    ├── interface_setup.png       # WAN/LAN configuration
    ├── firewall_rules.png        # Rule configuration
    └── traffic_test.png          # Testing from Kali
```

---

## 📜 Academic Context

| Detail | Info |
|--------|------|
| Module | Network Security |
| Institution | UCLan / NCC Education |
| Level | Undergraduate |
| Year | 2025–2026 |

---

## ⚠️ Disclaimer

This project was developed strictly for educational purposes in a controlled lab environment. All configurations were tested in an isolated VMware network.

---

## 👤 Author

**Ahmad Mourad** — Cybersecurity & Networking Student

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ahmad-mourad-775384381)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Ahmad-Cyber8)
