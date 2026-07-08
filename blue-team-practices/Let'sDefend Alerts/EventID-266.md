# 📄 SOC Incident Report

## 📌 General Information

- **Platform:** Let's Defend
- **Analyst:** Juan J. Donado A.
- **Event ID:** 266
- **Type:** Generic
- **Date:** Jun, 11, 2024, 01:40 PM
- **Rule Name**: SOC290 - EDR and Security Tools Process Enumeration
- **Severity:** Medium
- **Level**: Incident Responder
- **Source Address:** 172.16.17.177
- **Hostname:** Diana
- **Malicious IP:** 89.187.171.229
- **Process Path:** /usr/bin/ps
- **Parent Process:** bash
- **Command Line:** ps aux | grep falcon-sensor
- **Trigger Reason:** Detected unauthorized enumeration of EDR and security tool processes using system commands.
- **Device Action:** Allowed

## 🚨 Alert Description

A brute force attack was observed on the Diana host. Following the brute force attempt, suspicious commands were executed on the system. Escalating for detailed analysis.

# 📂 Logs & Evidence

Action Details: Jun 11 13:36:14 ip-172-16-17-177 sshd[2322]: ==Invalid user== admin from 89.187.171.229 port 13291

Action Details: Jun 11 13:36:38 ip-172-16-17-177 sshd[3699]: ==Failed password== for diana from 89.187.171.229 port 10793 ssh2

Action Details: Jun 11 13:39:59 ip-172-16-17-177 sshd[3699]: ==Accepted== password for diana from 89.187.171.229 port 10793 ssh2

**ssh Log:** Juna 1 13:39:57 ip-172-31-19-177 sshd[3639]: Accepted password for diana from ==89.187.171.229== port 10793 ssh2

| Source    | Key Evidence               |
| --------- | -------------------------- |
| Auth Logs | Multiple failures + Sucess |
| endpoint  | EDR/XDR Enumeration        |

# 🧠 Analysis

The event is a critical True Positive. The sequence of events is clear and alarming: 
- Brute Force: Multiple failed attempts followed by a successful login from IP address 89.187.171.229. 
- Post-Exploitation: Once inside, the attacker executed `ps aux | grep falcon-sensor` to identify if the EDR (CrowdStrike Falcon) was active. This indicates a technically savvy actor attempting to evade detection.

# ⚙️ Enrichment

- **IP reputation:** Suspicious but Brute force pattern is enough to say it is malicious.
- **GeoIP:** London UK
- **VirusTotal:** 1/93 security vendor flagged this IP address as malicious.
- **Threat Intel feeds:** None

# 🌐 MITRE ATT&CK Mapping

| Tactic                         | Technique |
| ------------------------------ | --------- |
| System Service Discovery       | T1007     |
| Brute Force: Password Spraying | T1110.003 |

# 🔧 Response Actions

- Endpoint Isolation

# ✔️ Final Veredict

- **Incident Type:** Brute Force and EDR/XDR Enumertion.
- **Status:** Closed / Escalated
- **Confidence Level:** Medium

# 🛡️ Recommendation

- Improve detection rule
- Enable MFA
- Adjust alert thresholds

# 📝 Lessons Learned

Correct Rule setup on EDRs,Firewalls, etc.

