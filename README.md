# Virtual Home Cybersecurity Lab

## Overview
This project simulates a small-to-medium business (SMB) network environment, combining both offensive and defensive cybersecurity tools. The lab is designed to provide hands-on experience in system administration, endpoint security, intrusion detection, log analysis, incident response, and penetration testing. By creating a controlled environment, I can practice defending against real-world attacks while also exploring offensive tradecraft.

---

## Architecture / Topology
The lab environment consists of **servers, workstations, and security tools** deployed across virtual machines. It mimics a corporate infrastructure with employees, IT assets, and attackers interacting in the same network.

**Network Components:**
- **Workstations**
  - Employee Workstation (Windows 11 Enterprise, Wazuh Agent)
  - Employee Workstation (Ubuntu Desktop, Wazuh Agent)
  - Security Workstation (Security Onion)
  - Attacker Machine (Kali Linux)

- **Servers**
  - Domain Controller / Active Directory (Windows Server 2025, Wazuh Agent)
  - Corporate Email Server (Ubuntu Desktop with MailHog + Docker)
  - Security Server (Ubuntu Server with Wazuh XDR & SIEM)

> **[Diagram Placeholder]** – A network diagram illustrating the above components and their interconnections.

---

## Environment & Tools

### Host System
- **Host OS**: Windows 11
- **Hypervisor**: VirtualBox
- **Storage**: 1TB external hard drive dedicated to VM storage

### Enterprise Tools & Defense
- **Microsoft Active Directory** – Directory service for managing network resources, users, and permissions in a Windows domain environment.
- **Wazuh** – Open-source SIEM and XDR for intrusion detection, vulnerability management, compliance reporting, and log analysis.
- **MailHog** – Lightweight email testing tool acting as a fake SMTP server, used to simulate enterprise mail flow and capture test messages.

### Offensive Tools
- **Evil-WinRM** – Post-exploitation WinRM client for interacting with Windows systems.
- **Hydra** – High-speed brute-force tool for testing authentication on multiple network protocols.
- **SecLists** – Extensive collection of penetration testing wordlists for reconnaissance and exploitation.
- **NetExec** – Lateral movement and remote command execution tool leveraging multiple protocols.
- **XFreeRDP** – Open-source Remote Desktop Protocol (RDP) client for post-exploitation access to Windows systems.

---

## Setup Instructions
1. Install VirtualBox on Windows 11.
2. Provision virtual machines stored on the 1TB external hard drive to ensure adequate space and performance.
3. Configure a private NAT/Host-only network to simulate an isolated corporate LAN.
4. Install and configure the following:
   - Windows Server 2025: Promote to Domain Controller and configure Active Directory.
   - Windows 11 Enterprise: Join to the domain; install Wazuh Agent.
   - Ubuntu Desktop: Install Wazuh Agent; set up Docker + MailHog.
   - Ubuntu Server: Deploy Wazuh SIEM/XDR server.
   - Security Onion: Configure sensors and Elastic Stack for monitoring.
   - Kali Linux: Install attack tools (Hydra, Evil-WinRM, SecLists, NetExec, XFreeRDP).
5. Integrate logging and monitoring with Wazuh & Security Onion.
6. Validate functionality by simulating attacks and verifying detection.

---

## Use Cases & Skills Learned
- **Blue Team Skills**
  - Active Directory administration and domain hardening.
  - Deploying and managing Wazuh for SIEM/XDR functions.
  - Email server simulation and log monitoring with MailHog.
  - Incident detection, log correlation, and alert triage with Security Onion.

- **Red Team Skills**
  - Brute-force and credential testing with Hydra.
  - Lateral movement and privilege escalation with NetExec & Evil-WinRM.
  - Exploitation and reconnaissance using SecLists and RDP (XFreeRDP).

---

## Future Improvements
- Add pfSense or OPNsense as a firewall for realistic perimeter defense.
- Expand with Splunk for log aggregation and SIEM comparison.
- Introduce honeypots for threat emulation.
- Automate lab deployment with Ansible or Terraform.

---

## References
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Security Onion Docs](https://securityonion.net/docs/)
- [MailHog GitHub](https://github.com/mailhog/MailHog)
- [Kali Linux Tools](https://www.kali.org/tools/)
- [SecLists GitHub](https://github.com/danielmiessler/SecLists)
