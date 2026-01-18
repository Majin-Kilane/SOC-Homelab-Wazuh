## 🛡️ SOC Homelab – Active Directory Monitoring with Wazuh SIEM

## 📌 Overview
This repository documents a Security Operations Center (SOC) homelab built around Wazuh SIEM. The lab focuses on detection, monitoring, and incident investigation across Active Directory infrastructure and domain-joined systems.

The SOC environment consumes logs and alerts from the Active Directory Home Lab, which serves as the monitored enterprise environment.
_____________________________________________________________________________________

## Objectives
1. Deploy and configure Wazuh SIEM in an internal network
2. Monitor Active Directory Domain Controllers and clients
3. Implement File Integrity Monitoring (FIM)
4. Centralize Windows event logging
5. Simulate attacks and validate detections
6. Practice SOC-style investigation workflows
7. Document alerts and incident response processes

This SOC environment is built on top of a separate Active Directory homelab, which serves as the infrastructure foundation.

🔗 Active Directory Infrastructure Repo:
👉 https://github.com/Majin-Kilane/Active-Directory

_____________________________________________________________________________________

## SOC Architecture

## Components
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
   - Network: Internal Network

![SOC Homelab Diagram](https://github.com/Majin-Kilane/SOC-Homelab-Wazuh/blob/main/SOC-Homelab-Wazuh.jpg?raw=true)

All assets reside on the same internal VirtualBox network to ensure secure, authenticated log collection.
_____________________________________________________________________________________

## Wazuh Deployment
**1. Wazuh Server Setup**
- Installed on Ubuntu Server
- Assigned static IP (192.168.1.104)
- Internal-only network connectivity
- DNS forwarding enabled via AD for updates

**2. Wazuh Agent Deployment**
- Agents installed on:
  - HL-DC
  - ADFO
  - Windows 11 Client
- Agent installation automated using **Group Policy (GPO)**
- Separate GPOs used for:
  - Agent installation
  - Agent configuration (SIEM IP, service management)

![Active Agents](https://github.com/Majin-Kilane/SOC-Homelab-Wazuh/blob/main/AllAgents.PNG?raw=true)
_____________________________________________________________________________________

## File Integrity Monitoring (FIM)
**Purpose**

Detect unauthorized or suspicious changes to critical system and Active Directory files.

**Monitored Paths**
- C:\Windows\System32
- C:\Windows\SYSVOL
- C:\Program Files
- C:\Program Files (x86)
- C:\Users\Public

**Detection**
- File creation, deletion, modification
- Permission changes
- Hash comparison


_____________________________________________________________________________________

## Alerting & Investigation Workflow

1. Alert triggered in Wazuh Dashboard
2. Analyst reviews affected host and file
3. Correlates with authentication and process events
4. Determines legitimacy of change
5. Documents or escalates incident




















___________________________________________________________________________________

_____________________________________________________________________________________

## 🔗 Related Project

This SOC lab is built on top of the following infrastructure project:

**👉 Active Directory Homelab**
https://github.com/Majin-Kilane/Active-Directory
















