

---

# Virtual Home Cybersecurity Lab

## Overview

This project simulates a small-to-medium business (SMB) network environment, combining both **offensive** and **defensive** cybersecurity tools. The lab provides hands-on experience in system administration, endpoint security, intrusion detection, log analysis, incident response, and penetration testing. By creating a controlled environment, I can practice defending against real-world attacks while also exploring offensive tradecraft.

---

## Architecture / Topology

The lab environment consists of **servers, workstations, and security tools** deployed across virtual machines. It mimics a corporate infrastructure with employees, IT assets, and attackers interacting in the same network.

**Network Components**

* **Workstations**

  * Windows 11 Enterprise (with Wazuh Agent)
  * Ubuntu Desktop (with Wazuh Agent)
  * Security Onion (dedicated monitoring workstation)
  * Kali Linux (attacker machine)

* **Servers**

  * Windows Server 2025 – Domain Controller / Active Directory (with Wazuh Agent)
  * Ubuntu Desktop – Corporate Email Server (MailHog + Docker)
  * Ubuntu Server – Security Server (Wazuh XDR & SIEM)

---

## Diagrams

To make the architecture easier to understand, diagrams are provided to show different perspectives of the lab.

### 1. Topology Overview

High-level network diagram of servers, workstations, and attacker machine.
![Topology Overview](docs/topology.png)

### 2. Operating Systems

Visual breakdown of which operating systems are running on each node.
![Operating Systems](docs/operating-systems.png)

### 3. Process Flow

Example: Wazuh SIEM workflow from **workstation agent → security server → alert notification**.
![Process Flow](docs/wazuh-flow.png)

> 📌 *All diagrams are located in the `/docs` folder.*

---

## Environment & Tools

### Host System

* **OS**: Windows 11
* **CPU**: Intel i7 (10 cores)
* **RAM**: 16GB
* **Storage**: 1TB external SSD (VM storage)
* **Hypervisor**: VirtualBox

### Defensive Tools

* **Microsoft Active Directory** – Centralized authentication and access control.
* **Wazuh (XDR & SIEM)** – Intrusion detection, log collection, vulnerability management.
* **Security Onion** – Network security monitoring with Elastic Stack.
* **MailHog** – Lightweight SMTP testing tool to simulate enterprise mail flow.

### Offensive Tools

* **Hydra** – Brute-force testing on multiple protocols.
* **Evil-WinRM** – Post-exploitation tool for Windows systems.
* **NetExec** – Lateral movement and remote command execution.
* **SecLists** – Collection of wordlists for reconnaissance and exploitation.
* **XFreeRDP** – Open-source RDP client for post-exploitation access.

---

## Setup Instructions

1. Install **VirtualBox** on the Windows 11 host.
2. Create virtual machines on the external SSD to optimize performance.
3. Configure a **NAT/Host-only private network** to simulate an isolated LAN.
4. Provision VMs:

   * Windows Server 2025 – Configure AD DS and promote to Domain Controller.
   * Windows 11 Enterprise – Join to domain; install Wazuh Agent.
   * Ubuntu Desktop – Install Wazuh Agent; deploy MailHog via Docker.
   * Ubuntu Server – Deploy Wazuh SIEM/XDR.
   * Security Onion – Configure sensors and Elastic Stack.
   * Kali Linux – Install Hydra, Evil-WinRM, NetExec, SecLists, and XFreeRDP.
5. Integrate logging with **Wazuh** and **Security Onion**.
6. Validate the environment by simulating attacks and verifying detections.

---

## Use Cases & Skills Learned

**Blue Team Skills**

* Active Directory administration and hardening.
* SIEM/XDR deployment with Wazuh.
* Network and log monitoring with Security Onion.
* Incident detection, correlation, and triage.

**Red Team Skills**

* Credential testing and brute-force (Hydra).
* Post-exploitation and lateral movement (Evil-WinRM, NetExec).
* Reconnaissance and exploitation with SecLists and RDP access.

---

## Future Improvements

* Add **pfSense/OPNsense** for perimeter firewalling.
* Expand with **Splunk** for SIEM comparison.
* Deploy **honeypots** to study attacker behavior.
* Automate provisioning with **Ansible/Terraform**.

---

## References

* [Wazuh Documentation](https://documentation.wazuh.com/)
* [Security Onion Docs](https://securityonion.net/docs/)
* [MailHog GitHub](https://github.com/mailhog/MailHog)
* [Kali Linux Tools](https://www.kali.org/tools/)
* [SecLists GitHub](https://github.com/danielmiessler/SecLists)

---


