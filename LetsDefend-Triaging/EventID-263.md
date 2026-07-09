![letsdefend-logo](images/letsdefend-logo.png)

# EventID 263 - Security Triage Report

## Summaryc

- **EventID :** 263
- **Event Time :** Jun, 06, 2024, 03:12 PM
- **Rule :** SOC287 - Arbitrary File Read on Checkpoint Security Gateway [CVE-2024-24919]
- **Severity:** High
- **Level :** Security Analyst
- **Hostname :** CP-Spark-Gateway-01
- **Primary User:** admin
- **Last Login:** Jun, 05, 2024, 09:05 AM
- **Destination IP Address :** 172.16.20.146
- **Source IP Address :** 203.160.68.12
- **HTTP Request Method :** POST
- **Requested URL :** 172.16.20.146/clients/MyCRL
- **Request :** aCSHELL/../../../../../../../../../../etc/passwd
- **User-Agent :** Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:126.0) Gecko/20100101 Firefox/126.0
- **Alert Trigger Reason :** Characteristics exploit pattern Detected on Request, indicative exploitation of the CVE-2024-24919.
- **Device Action :** Allowed

---

## Actions Taken

- **CVE Research:** Research on CVE-2024-24919 via external sources to analyze public exploits and vendor advisories.
- **Log Analysis:** Correlated with OS logs.
- **Treat enrichment:** Checked external IP reputation on Virus total .
- **Containment Actions:** Isolated host via Endpoint security containment tool provided by LetsDefend.

---

## Findings

**Public CVE exploit:** https://github.com/verylazytech/CVE-2024-24919

**Related logs:** 

	LOGFILE: /var/log/access.log
	
	203.160.68.12 : - - [06/Jun/2024:15:12:43 +0000] "GET /clients/MyCRL HTTP/1.1" 200 452 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:126.0) Gecko/20100101 Firefox/126.0"
	
	203.160.68.12 : - - [06/Jun/2024:15:12:45 +0000] "POST /clients/MyCRL HTTP/1.1" 200 1256 "aCSHELL/../../../../../../../../../../etc/passwd" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:126.0) Gecko/20100101 Firefox/126.0"
	
	192.168.1.100 : - - [06/Jun/2024:15:13:01 +0000] "GET / HTTP/1.1" 404 234 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Safari/537.36"
	
	10.0.0.5 : - - [06/Jun/2024:15:13:20 +0000] "POST / HTTP/1.1" 201 1024 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Safari/537.36"
	
	172.16.20.50: - - [06/Jun/2024:15:13:45 +0000] "GET / HTTP/1.1" 200 678 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:87.0) Gecko/20100101 Firefox/87.0"
	
	203.160.68.13 : - - [06/Jun/2024:15:14:02 +0000] "POST /clients/MyCRL HTTP/1.1" 403 314 "aCSHELL/../../../../../../../../../../etc/shadow" "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:126.0) Gecko/20100101 Firefox/126.0"
	
	10.0.0.10 : - - [06/Jun/2024:15:14:30 +0000] "GET /index.html HTTP/1.1" 200 854 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:88.0) Gecko/20100101 Firefox/88.0"
	
	203.160.68.12 : - - [06/Jun/2024:15:15:01 +0000] "POST / HTTP/1.1" 200 512 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:126.0) Gecko/20100101 Firefox/126.0"

**External IP Reputation:** 6/91 security vendors flagged this IP address as malicious - https://www.virustotal.com/gui/ip-address/203.160.68.12

---

## MITRE ATT&CK Mapping

- **T1190** - Exploit Public-Facing Application.
- **T1003** - OS Credential Dumping.

---

## Decision & Justification

**Final Status:** ESCALATED

**Justification:**  The alert has been validated as a True Positive. Network logs confirm deliberate exploitation attempts targeting CVE-2024-24919 against the Check Point Security Gateway (`172.16.20.146`) from external IPs `203.160.68.12` and `203.160.68.13`. The primary attack vector included a well-known path traversal payload (`aCSHELL/../../etc/passwd`) targeting `/clients/MyCRL`.

Although the second attempt for `/etc/shadow` was successfully blocked (HTTP 403), the initial request returned an HTTP 200 status code with a significant payload size (1256 bytes). Due to the high probability of data exfiltration of local system files, immediate escalation and incident response protocols are required.

---

## Recommendation

**Apply Vendor Patches**: Install the official manufacturer hotfix (Check Point) for the affected Gaia OS version immediately.

---

## Lessons Learned

**Prioritized Patch Management:** Classify vulnerabilities affecting edge assets and critical infrastructure as Tier 1 threats. Establish an accelerated patching window (e.g., within 24–48 hours of disclosure) to mitigate exposure before active exploitation begins.