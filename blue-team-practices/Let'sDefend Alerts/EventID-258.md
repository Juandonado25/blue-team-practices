# 📄 SOC Incident Report

## 📌 General Information

- **Platform:** Let's Defend
- **Analyst:** Juan J. Donado A.
- **Event ID:** 258
- **Type:** Malware
- **Date:** May, 14, 2024, 08:42 AM
- **Rule Name**: SOC281 - System Network Configuration Discovery Detected
- **Severity:** Low
- **Level**: Incident Responder
- **Source Address:** 172.16.17.97
- **Destination Address:** 52.219.102.10
- **Destination Hostname:**
- **Alert Trigger Comand:** C:\Windows\system32\cmd.exe /c ipconfig /all
- **Current Directory:** C:\Users\LetsDefend\Downloads\cleaner\
- **Parent CommandLine:** C:\Users\LetsDefend\Downloads\20\20.exe
- **Suspicious Mail Address:** jame@cleanpatron.top
- **URL:** hxxps[://]files-ld[.]s3[.]us-east-2[.]amazonaws[.]com/cleaner[.]zip

## 🚨 Alert Description

Process uses IPCONFIG to discover network configuration.

# 🔎 Investigation Process

Step by step, like a real SOC.
1. Alert Validation
2. Log review
3. IP Reputation check
4. User behavior analysis

# 📂 Logs & Evidence


| Source    | Key Evidence               |
| --------- | -------------------------- |
| Auth Logs | Multiple failures + Sucess |
| Firewall  | Ip not previously seen     |
| endpoint  | No malware detected        |

# 🧠 Analysis

Was this a true positive or false positive
Why?
Any correlation with other alerts?

# ⚙️ Enrichment

- **IP reputation:**
- **GeoIP:**
- **VirusTotal:**
- **Threat Intel feeds:**

# 🌐 MITRE ATT&CK Mapping

| Tactic            | Technique |
| ----------------- | --------- |
| Credential Access | T1110     |
| Initial Access    | T1078     |

# ❗ Impact Assessment

- **User impacted:** Andrew
- **Systems affected:**
- **Data exposure risk:**

# 🔧 Response Actions

- Account reset
- IP blocked
- Ticket escalated
- monitoring enabled

# ✔️ Final Veredict

- **Incident Type:** (Brute Force / Phishing / Benign)
- **Status:** Closed / Escalated
- **Confidence Level:** High / Medium

# 🛡️ Recommendation

- Improve detection rule
- Enable MFA
- Adjust alert thresholds

# 📝 Lessons Learned

What to improve as a SOC.

