# Virtual Home Cybersecurity Lab

<p align="center">
  <a href="https://www.virtualbox.org/"><img src="https://img.shields.io/badge/VirtualBox-Lab-blue"></a>
  <a href="https://www.comptia.org/certifications/security"><img src="https://img.shields.io/badge/Certification-Security%2B-red"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green"></a>
</p>


---

## Table of Contents
- [Overview](#overview)
- [Architecture / Topology](#architecture--topology)
- [Interconnections](#interconnections)
- [Environment & Tools](#environment--tools)
- [Lab Setup & Configuration](#lab-setup--configuration)
  - [Planned Detailed Guides](#planned-detailed-guides)
- [Use Cases & Skills Learned](#use-cases--skills-learned)
- [Future Improvements](#future-improvements)
- [References](#references)

---

## Overview
This project simulates a **small-to-medium business (SMB) network** environment, combining both **offensive** and **defensive** cybersecurity tools.  

It provides hands-on experience in:
- System administration  
- Endpoint security  
- Intrusion detection  
- Log analysis  
- Incident response  
- Penetration testing  

By creating a controlled environment, I can practice defending against real-world attacks while also exploring offensive tradecraft.

---

## Architecture / Topology
The lab consists of **servers, workstations, and security tools** deployed across virtual machines. It mimics a corporate infrastructure with employees, IT assets, and attackers on the same network.

![Topology Overview](docs/Virtual_Home_Lab_Diagram.png)
Figure 1 – Network topology for the virtual cybersecurity lab, showing servers, workstations, and attacker machine.
### Network Components

**Workstations**
- **Windows 11 Enterprise (Employee)** – Standard workstation with Wazuh Agent.  
- **Ubuntu Desktop (Employee)** – Alternative workstation with Wazuh Agent.  
- **Security Onion** – Network security monitoring workstation.  
- **Kali Linux** – Attacker machine for penetration testing.  

**Servers**
- **Windows Server 2025 (Domain Controller)** – Active Directory, authentication, log forwarding via Wazuh Agent.  
- **Ubuntu Desktop (MailHog + Docker)** – Corporate email server simulation.  
- **Ubuntu Server (Wazuh SIEM/XDR)** – Centralized log collection and analysis.  

---

## Interconnections

* **Workstations → Domain Controller** – Authentication for network resources.  
* **Workstations → Email Server** – Sending/receiving emails.  
* **Workstations → Security Server** – Log forwarding via Wazuh Agent.  
* **Security Onion → All Servers** – Monitors traffic and logs.  
* **Domain Controller → Security Server** – Security logs via Wazuh Agent.  
* **Email Server → Security Server** – Security logs for email traffic.  
* **Attacker → All Components** – Simulated attacks for testing defenses.  

---

## Environment & Tools

### Host System
* **OS**: Windows 11  
* **CPU**: Intel i7 (10 Cores)  
* **RAM**: 16 GB  
* **Hypervisor**: VirtualBox  
* **Storage**: 1TB external SSD (VM storage)  

### Defensive Tools
* **Active Directory** – User and resource management.  
* **Wazuh** – SIEM/XDR for intrusion detection and log analysis.  
* **MailHog** – Fake SMTP server for testing email flow.  
* **Security Onion** – Network monitoring and Elastic Stack log analysis.  

### Offensive Tools
* **Evil-WinRM** – Post-exploitation WinRM client.  
* **Hydra** – Brute-force tool for authentication testing.  
* **SecLists** – Penetration testing wordlists.  
* **NetExec** – Lateral movement and remote execution.  
* **XFreeRDP** – Open-source RDP client for exploitation and post-access.  

---

## Lab Setup & Configuration
This section currently provides a **high-level summary** of setup. It will be expanded into a **full guide** with:

* Detailed **installation instructions** (per OS/tool)  
* **VM configurations** (CPU, memory, storage, networking)  
* **System requirements**  
* Step-by-step guides with **commands & screenshots**  
* **Troubleshooting tips**  

### Current Setup Summary
1. Install **VirtualBox** on Windows 11.  
2. Provision VMs on the external SSD.  
3. Configure NAT/Host-only network for isolation.  
4. Install and configure components:  
   * **Windows Server 2025** → Domain Controller + AD.  
   * **Windows 11 Enterprise** → Join domain, install Wazuh Agent.  
   * **Ubuntu Desktop** → Wazuh Agent + Docker + MailHog.  
   * **Ubuntu Server** → Wazuh SIEM/XDR.  
   * **Security Onion** → Configure Elastic Stack + sensors.  
   * **Kali Linux** → Hydra, Evil-WinRM, SecLists, NetExec, XFreeRDP.  
5. Integrate logs into **Wazuh** and monitoring in **Security Onion**.  
6. Validate setup by simulating attacks and confirming detections.  

---

### Planned Detailed Guides
*(Coming Soon — placeholders for expansion)*  
* **Windows Server 2025 Setup**  
* **Ubuntu Server (Wazuh SIEM)**  
* **Security Onion Configuration**  
* **Kali Linux Toolset Setup**  
* **VM Performance Tuning**  

---

## Use Cases & Skills Learned

This virtual lab supports **cybersecurity training, testing, and experimentation**.

### Use Cases
* **Security Monitoring** – Detect suspicious activity across endpoints and servers.  
* **Attack Simulation** – Test and refine defensive measures.  
* **Training** – Safe environment for practicing monitoring and IR workflows.  
* **Vulnerability Assessment** – Identify and validate weaknesses.  
* **Incident Response** – Practice response procedures and log correlation.  

<details>
<summary>Blue Team Skills</summary>

- Active Directory administration and domain hardening  
- Deploying and managing Wazuh SIEM/XDR  
- Email server simulation with MailHog  
- Log correlation, alert triage, and traffic analysis in Security Onion  

</details>

<details>
<summary>Red Team Skills</summary>

- Brute-force authentication testing with Hydra  
- Lateral movement and privilege escalation via NetExec & Evil-WinRM  
- Reconnaissance and exploitation with SecLists + RDP  

</details>

<details>
<summary>Purple Team Skills</summary>

- Map red team techniques to blue team detections (MITRE ATT&CK)  
- Validate SIEM rules against simulated attacks  
- Improve log sources and detection coverage  
- Create a feedback loop between red and blue activities  

</details>


**Example Scenario:**  
> Simulate brute-force logins from Kali → Detect failed logins in Wazuh → Tune alert rules in Security Onion.  

---

## Future Improvements (Roadmap)

**Near Term**
* Add **pfSense/OPNsense** firewall for perimeter defense.  
* Begin **Splunk integration** for SIEM comparison.  

**Mid Term**
* Deploy **honeypots** for threat emulation.  
* Expand user/endpoint diversity (macOS, mobile).  

**Long Term**
* Automate lab deployment with **Ansible/Terraform**.  
* Extend with **cloud-based services** (Azure/AWS testbed).  

---

## References
* [Wazuh Documentation](https://documentation.wazuh.com/)  
* [Security Onion Docs](https://securityonion.net/docs/)  
* [MailHog GitHub](https://github.com/mailhog/MailHog)  
* [Kali Linux Tools](https://www.kali.org/tools/)  
* [SecLists GitHub](https://github.com/danielmiessler/SecLists)
* [Active Directory Docs](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)
* [VirtualBox Manual](https://www.virtualbox.org/manual/UserManual.html)
