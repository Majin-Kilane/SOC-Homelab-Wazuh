## 🛡️ SOC Homelab – Active Directory Monitoring with Wazuh SIEM

## 📌 Overview
This project demonstrates my Security Operations Center (SOC) homelab built to monitor an enterprise-style Active Directory environment using Wazuh SIEM.

The lab focuses on:

- Centralized log collection
- Identity-based threat detection
- Endpoint visibility
- Monitoring high availability services (DHCP failover)

This SOC environment is built on top of a separate Active Directory homelab, which serves as the infrastructure foundation.

🔗 Active Directory Infrastructure Repo:
👉 https://github.com/Majin-Kilane/Active-Directory

_____________________________________________________________________________________

## Architecture Overview

## Core Components
**HL-DC** – Primary Domain Controller
   - AD DS, DNS, DHCP (Primary)
   - IP: 192.168.1.10
**ADFO** – Failover Domain Controller
   - AD DS, DNS, DHCP (Failover)
   - IP: 192.168.1.11
**Windows 11 Client**
   - Domain-joined endpoint
   - IP assigned via DHCP
**Wazuh SIEM Server**
   - OS: Ubuntu Server 22.04
   - IP: 192.168.1.104 (DHCP-assigned)
   - Roles: Wazuh Manager, Indexer, Dashboard
   - Network: Internal Network (Oracle VirtualBox)

********ADD DIAGRAM*******
