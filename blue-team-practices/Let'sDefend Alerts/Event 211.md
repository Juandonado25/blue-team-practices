# 📄 SOC Incident Report

## 📌 General Information

- **Platform:** Let's Defend
- **Analyst:** Juan J. Donado A.
- **Event ID:** 211
- **Type:** Unauthorized Access
- **Date:** Dec, 22, 2023, 06:45 AM
- **Rule** Nam: SOC249 - Port Scan Detected
- **Severity:** Low
- **Level**: Incident Responder
- **Source Address:** 37.19.199.146
- **Destination Address:** 172.16.20.44
- **Destination Hostname:** WebServer-Test

## 🚨 Alert Description

Multiple requests are detected from the same address to the same destination IP with different ports in a short time.

# 🔎 Investigation Process

Step by step, like a real SOC.
1. Alert Validation
2. Log review
3. 

# 📂 Logs & Evidence

| Source   | Key Evidence                                                                                  |
| -------- | --------------------------------------------------------------------------------------------- |
| Firewall | External IP performed port scan against internal host, probing multiple TCP ports             |
| Proxy    | Multiple failed HTTP requests to different paths fro same source IP indicating reconnaissance |
| endpoint | No malware detected                                                                           |

# 🧠 Analysis

It is a True Positive for Port Scanning

# ⚙️ Enrichment

- **IP reputation:**  suspicious 
- **GeoIP:** London, United Kingdom
- **VirusTotal:** 1/95 security vendor flagged this IP address as malicious.

# 🌐 MITRE ATT&CK Mapping

| Tactic         | Technique |
| -------------- | --------- |
| Reconnaissance | T1595     |
| Reconnaissance | T1595.002 |

# ❗ Impact Assessment

- **User impacted:** 
- **Systems affected:**
- **Data exposure risk:**

# 🔧 Response Actions

- IP blocked
- monitoring enabled

# ✔️ Final Veredict

- **Incident Type:** (Brute Force / Phishing / Benign)
- **Status:** Closed / Escalated
- **Confidence Level:** High / Medium

# 🛡️ Recommendation

- Improve detection rule

# 📝 Lessons Learned

What to improve as a SOC.

