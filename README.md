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
   - IP: 192.168.1.100 (DHCP-assigned)
     
**Wazuh SIEM Server**
   - OS: Ubuntu Server 22.04
   - IP: 192.168.1.104 (DHCP-assigned)
   - Roles: Wazuh Manager, Indexer, Dashboard
   - Network: Internal Network (Oracle VirtualBox)

![SOC Homelab Diagram](https://github.com/Majin-Kilane/SOC-Homelab-Wazuh/blob/main/SOC-Homelab-Wazuh.jpg?raw=true)


_____________________________________________________________________________________

## 🌐 Network Design

- All systems communicate over an isolated internal network
- Wazuh ingests logs from:
   - Domain Controllers
   - Domain-joined Windows client
- No direct internet exposure for SIEM services

**Agent Communication:**
- TCP 1514 – Log ingestion
- TCP 1515 – Agent registration

_____________________________________________________________________________________

## ⚙️ Power-On Order (Best Practice)

1. HL-DC (Primary DC)
2. ADFO (Optional)
3. Wazuh Server
4. Windows 11 Client

This ensures DNS, AD authentication, and security logs are available before SIEM configuration.

_____________________________________________________________________________________

## 🔐 Wazuh Agent Deployment

**Domain Controllers**
Wazuh agents are installed on:
- HL-DC
- ADFO

**Monitored Events:**
- Authentication failures
- Account lockouts
- Privileged group changes
- Kerberos activity
- DNS and DHCP-related events

_____________________________________________________________________________________

## Windows 11 Client

The Wazuh agent provides:
- Logon/logoff monitoring
- Process execution tracking
- PowerShell detection
- Registry change visibility

📸 Add Image Here: Wazuh Dashboard showing active agents

_____________________________________________________________________________________

## 🚨 SOC Detection Use Cases

**1. Brute-Force Authentication**
- Detect repeated failed login attempts
- Alert on account lockouts

**2. Privilege Escalation**
- Detect changes to Domain Admins group
- Alert on unauthorized group membership changes

**3. Endpoint Threat Activity**
- Suspicious PowerShell execution
- Unauthorized binaries

**3. Infrastructure & Failover Monitoring**
- DHCP service failure
- Domain controller availability
- Authentication continuity during failover

📸 Add Image Here: Alert timeline showing correlated AD and endpoint events

_____________________________________________________________________________________

## 🧠 MITRE ATT&CK Mapping

| Technique ID | Description          |
| ------------ | -------------------- |
| T1110        | Brute Force          |
| T1078        | Valid Accounts       |
| T1098        | Account Manipulation |
| T1059        | Command Execution    |

_____________________________________________________________________________________

## 📁 Repository Structure

SOC-Homelab-Wazuh/
├── diagrams/
├── setup-guides/
│   ├── wazuh-installation.md
│   ├── agent-deployment.md
│   └── alerting-configuration.md
│
├── detections/
│   ├── brute-force.md
│   ├── privilege-escalation.md
│   ├── failover-monitoring.md
│
├── fim/
│   └── file-integrity-monitoring.md
│
├── simulations/
│   └── ransomware-simulation.md
│
├── incident-reports/
│   └── incident-report-template.md
│
└── README.md


_____________________________________________________________________________________

## 🎯 Skills Demonstrated
- SIEM deployment and configuration
- Active Directory security monitoring
- Endpoint detection and response fundamentals
- Log analysis and alert triage
- High availability service awareness
- MITRE ATT&CK mapping

_____________________________________________________________________________________

## 🔗 Related Project

This SOC lab is built on top of the following infrastructure project:

**👉 Active Directory Homelab**
https://github.com/Majin-Kilane/Active-Directory
















