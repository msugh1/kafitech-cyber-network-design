<div align="center">

<img width="2560" height="562" alt="image" src="https://github.com/user-attachments/assets/61bc2b7a-4ca7-4db6-8f1f-01dcf90e7ab1" />

**VLAN-segmented • ACL-controlled • Layer 2 hardened network** implemented in **Cisco Packet Tracer**

[![Cisco](https://img.shields.io/badge/Platform-Cisco%20Packet%20Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)](https://www.netacad.com/courses/packet-tracer)
[![Security](https://img.shields.io/badge/Security-Layer%202%20%26%203-brightgreen?style=for-the-badge&logo=shield&logoColor=white)](#)
[![VLANs](https://img.shields.io/badge/VLANs-10%2C20%2C30%2C40%2C50%2C70-blue?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

</div>

---

## 📌 Project Overview

Kafitech Solutions required a **cyber-resilient network architecture** to securely connect five departments while providing controlled guest access.

This project delivers a production-grade design featuring:

- Departmental VLAN isolation (Software Dev, HR, Finance, IT Support, Management)
- Strict inter-VLAN Access Control Lists (ACLs)
- Full Layer-2 switch hardening
- Dual SSID wireless (Corporate + Guest isolation)
- DMZ web server with restricted access
- Device hardening (SSH-only, banners, encrypted passwords)
- Centralized logging (Syslog + SNMPv3 simulation)

---
## 📑 Table of Contents

- [📌 Project Overview](#-project-overview)
- [🏗️ Network Topology](#%EF%B8%8F-network-topology)
- [📊 IP Addressing Scheme](#-ip-addressing-scheme)
- [🔒 Key Security Controls](#-key-security-controls)
  - [Layer 3 – Access Control Lists](#layer-3--access-control-lists)
  - [Layer 2 – Switch Hardening](#layer-2--switch-hardening)
  - [Wireless Security](#wireless-security)
- [📁 Repository Contents](#-repository-contents)
- [✅ Validation](#-validation)
- [🚀 Real-World Recommendations](#-real-world-recommendations)
- [⭐ Support](#-support)
- [📄 License](#-license)

---

## 🏗️ Network Topology

![Network Topology](docs/topology/network-topology.png)

> *Full topology diagram available in the [docs](docs/) folder.*

---

## 📊 IP Addressing Scheme

| Department              | VLAN ID | Subnet            | Gateway         |
|-------------------------|---------|-------------------|-----------------|
| Software Development    | 10      | 192.168.10.0/24   | 192.168.10.1    |
| Human Resources         | 20      | 192.168.20.0/24   | 192.168.20.1    |
| Finance                 | 30      | 192.168.30.0/24   | 192.168.30.1    |
| IT Support              | 40      | 192.168.40.0/24   | 192.168.40.1    |
| Management              | 50      | 192.168.50.0/24   | 192.168.50.1    |
| Guest Wireless          | 70      | 192.168.70.0/24   | 192.168.70.1    |
| DMZ (Web Server)        | N/A     | 203.0.113.0/24    | 203.0.113.1     |

---

## 🔒 Key Security Controls

### Layer 3 – Access Control Lists
- **HR ↔ Finance**: Mutual blocking
- **Developers**: Only own VLAN + DMZ web server
- **IT Support**: Denied access to Management VLAN
- **Guests**: Internet-only (blocked from all internal networks)

### Layer 2 – Switch Hardening
| Feature              | Configuration                  | Protects Against          |
|----------------------|--------------------------------|---------------------------|
| Port Security        | Sticky MAC (1 device) + shutdown | Unauthorized devices     |
| BPDU Guard           | Enabled on edge ports          | Rogue switches            |
| DHCP Snooping        | Trusted uplinks only           | Rogue DHCP servers        |
| Dynamic ARP Inspection | ARP validation               | ARP spoofing              |
| Storm Control        | 50% broadcast threshold        | Broadcast storms          |
| Unused Ports         | Shutdown + VLAN 999            | Physical tampering        |

### Wireless Security
| SSID             | Band   | VLAN | Security          | Extra Protections          |
|------------------|--------|------|-------------------|----------------------------|
| Corporate_WiFi   | 5 GHz  | 60   | WPA2-PSK (AES)    | Hidden SSID + MAC filtering |
| Guest_WiFi       | 2.4 GHz| 70   | WPA2-PSK (AES)    | Client isolation           |

---

## 📁 Repository Contents

- [`docs/full-report.pdf`](docs/full-report.pdf) → Complete original project report
- [`docs/topology/`](docs/topology/) → Network diagrams
- [`docs/screenshots/`](docs/screenshots/) → Ping tests & verification
- [`configs/`](configs/) → Sample switch, router ACL, and wireless configurations

---

## ✅ Validation

- Extensive ping tests confirming permitted and blocked traffic flows
- Simulated attacks (rogue DHCP, ARP spoofing) successfully mitigated by Layer-2 protections
- All security policies verified in Packet Tracer

---

## 🚀 Real-World Recommendations

The report includes detailed recommendations for production deployment:
- Replace ACLs with Next-Generation Firewall
- Upgrade to WPA3-Enterprise + 802.1X (Cisco ISE / FreeRADIUS)
- Deploy SIEM (Splunk / ELK)
- Add High Availability (HSRP / StackWise)
- Implement Zero Trust & DLP

See the full report for the complete list.

---

## ⭐ Support

If this project helped you with your own Packet Tracer / CCNA / cybersecurity studies, please consider giving it a ⭐!

---

## 📄 License

This project is released under the MIT License. See [LICENSE](LICENSE) for details.
