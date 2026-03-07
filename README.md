```markdown
# AgroDefend: SOC in a Segmented Network

## 🛡️ Project Overview

AgroDefend is a hands-on cybersecurity project focused on designing and deploying a Security Operations Center (SOC) within a segmented network environment. The goal is to simulate real-world attack scenarios, detect threats using a SIEM solution, and demonstrate the effectiveness of network segmentation in containing breaches.

This project showcases the integration of **pfSense**, **Wazuh SIEM**, and multiple endpoint operating systems to build a defense-in-depth strategy aligned with the **MITRE ATT&CK Framework**.

---

## 🏗️ Network Architecture

The environment is built using a **three-tier network segmentation** model:

| Segment | Subnet       | Purpose                          |
|---------|--------------|----------------------------------|
| WAN     | 192.168.4.0/24| Simulated external/untrusted network |
| DMZ     | 192.168.5.0/24| Hosts public-facing services (Ubuntu) |
| LAN     | 192.168.1.0/24| Internal trusted network (Windows 10) |

- **Core Firewall/Router:** pfSense  
- **SIEM Platform:** Wazuh (Manager + Indexer + Dashboard)  
- **Endpoints:** Ubuntu Server (DMZ), Windows 10 (LAN), Kali Linux (Attacker)

![Network Diagram](link-to-your-image)

---

## 🧰 Tools & Technologies

| Tool         | Purpose                                  |
|--------------|------------------------------------------|
| pfSense      | Firewall, router, network segmentation   |
| Wazuh        | SIEM, log aggregation, threat detection  |
| Ubuntu 20.04 | DMZ server hosting SSH and FTP services  |
| Windows 10   | LAN endpoint for lateral movement testing|
| Kali Linux   | Attack simulation (Nmap, Hydra)          |
| MITRE ATT&CK | Threat mapping and classification        |

---

## 🚀 Key Implementations

### 1. Wazuh Deployment
- Installed **Wazuh Manager**, **Indexer**, and **Dashboard** on the LAN segment.
- Deployed **Wazuh Agents** on Ubuntu (DMZ) and Windows 10 (LAN).
- Verified connectivity and agent status via CLI and Wazuh Dashboard.

### 2. Attack Simulations

#### 🔐 SSH Brute Force Attack
- **Tool:** Hydra (from Kali Linux in WAN)
- **Target:** Ubuntu DMZ server (SSH on port 22)
- **Outcome:** Successful login detected → Wazuh triggered **Rule ID 40112** (High Severity - Level 12)

#### 📁 FTP Brute Force Attack
- **Tool:** Hydra
- **Target:** vsftpd service on Ubuntu DMZ
- **Outcome:** Similar alert generated, confirming credential compromise

#### 🔁 Lateral Movement Attempt
- Compromised DMZ host attempted to scan internal LAN manager.
- **Mitigation:** pfSense firewall rule blocking all DMZ → LAN traffic by default (except specific Wazuh agent communication on port 1514).

---

## 📊 Detection & Analysis

### Sample Alert: SSH Brute Force Success
- **Timestamp:** Feb 20, 2026 - 08:01:25
- **Attacker IP:** 192.168.4.11 (WAN)
- **Target IP:** 192.168.5.1 (DMZ Ubuntu)
- **Rule Level:** 12 (High Severity)
- **MITRE Mapping:** T1110 - Brute Force (Credential Access, Initial Access)

![Wazuh Alert Example](link-to-image)

---

## 🧠 Lessons Learned

- **Segmentation works:** The DMZ-to-LAN block prevented the attacker from pivoting internally.
- **SIEM visibility is critical:** Wazuh correlated failed + successful logins to detect the breach.
- **Password-based authentication is risky:** Even with segmentation, weak credentials can lead to compromise.
- **Defense-in-depth is essential:** Firewall rules + SIEM alerts + endpoint hardening = stronger security posture.

---

## ✅ Recommendations

1. **Disable password-based SSH** – Enforce key-based authentication only.
2. **Implement Multi-Factor Authentication (MFA)** – Especially for admin access.
3. **Enable account lockout policies** – Use fail2ban or OS-level controls.
4. **Maintain strict egress filtering** – Only allow necessary traffic between zones.
5. **Continuous monitoring** – Regularly review Wazuh alerts and update detection rules.

---

## 📁 Repository Structure

```
AgroDefend-SOC/
├── README.md
├── diagrams/
│   └── network-architecture.png
├── configs/
│   ├── pfSense-rules.txt
│   ├── wazuh-agent-config.txt
│   └── vsftpd-config.txt
├── alerts/
│   └── sample-alerts.json
├── reports/
│   └── AgroDefend-Final-Report.pdf
└── scripts/
    └── brute-force-sim.sh
```

---

## 📌 Acknowledgments

This project was developed as part of a hands-on cybersecurity simulation to demonstrate the value of SOC operations, network segmentation, and SIEM-based threat detection in a controlled lab environment.

---

## 📬 Contact

For questions, feedback, or collaboration opportunities, feel free to reach out:

- **GitHub:** [yourusername](https://github.com/yourusername)
- **LinkedIn:** [Your Name](https://linkedin.com/in/yourprofile)
- **Email:** your.email@example.com

---

> *"Defense in depth is not just about layers—it's about visibility, detection, and rapid response."*
```

You can copy this entire block and save it as `README.md` for your GitHub repository. Just remember to replace the placeholder links (like `link-to-your-image`) and contact information with your actual details.
