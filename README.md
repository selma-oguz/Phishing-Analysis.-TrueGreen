# SOC Incident Ticket: Phishing & Brand Impersonation Analysis

**Ticket ID:** INC-PHISH-001
**Date:** 7.9.2026
**Analyst:** Selma Oguz

## SECTION 1: Incident Summary and Email Description
######################################################

**Header Analysis Link:** [MXToolBox Analysis](https://mxtoolbox.com/Public/Tools/EmailHeaders.aspx?huid=4ba6748e-2bee-447b-b3b9-95b03b1dacb7)

On March 21, 2026, an internal user (`[REDACTED_USER]@yahoo.com`) received an unsolicited promotional email offering "6 weeks of free lawn care." The email attempts to impersonate the legitimate US-based lawn care company, TruGreen. 

**Analyst Observations:**
* **Geographical Anomaly:** The impersonated brand (TruGreen) is a US-based entity. However, the sender utilizes a UK-registered domain (`.co.uk`) and the sending server IP (`213.254.170.16`) is geolocated to a hosting provider in Turkey. This complete geographic mismatch is a strong indicator of fraudulent infrastructure.
* **Infrastructure Red Flags:** The sender IP lacks a Reverse DNS (PTR) record. A server identifying itself without a matching PTR record is a classic signature of rented, temporary, or compromised spam infrastructure.
* **Brand Inconsistencies:** The logo embedded in the email body is a spoofed version and does not match the official corporate branding of TruGreen.
* **Threat Intelligence:** The sending IP has been flagged as suspicious by at least one vendor on VirusTotal. 

**Impact Assessment:** 
No user interaction (clicks) occurred, and log analysis indicates no other employees received similar emails. 

### A) Email Artifacts (Observables)
=================================
* **Sending Address:** `hqhxmikwxezmqnc[@]charitablemere[.]co[.]uk`
* **Subject Line:** `6 ᴡᴇᴇᴋꜱ ᴏꜰ_ꜰ ʀ ᴇ ᴇ_ʟᴀᴡɴ ᴄᴀʀᴇ ᴡɪᴛʜ ᴄᴏᴅᴇ 6ᴡᴇᴇᴋꜱ* ᴏɴ ʏᴏᴜʀ ʟᴀᴡɴ ᴘʟᴀɴ....`
* **Recipients:** `[REDACTED_USER]@yahoo.com`
* **Sending Server IP:** `213[.]254[.]170[.]16`
* **Reverse DNS (PTR):** DNS Record not found
* **Reply-to:** `hqhxmikwxezmqnc[@]charitablemere[.]co[.]uk`
* **Date and Time:** Sat, 21 Mar 2026 15:59:51 -0400
* **Message ID:** `21032026155951288644638019_21032026155951947393438980@charitablemere.co.uk`

### B) Web Artifacts (Observables)
==============================
* **Full URL Links (Defang-sanitized):** 
  * `hxxp[://]fzrd[.]charitablemere[.]co[.]uk/3863907yI17602479aS694127584ck8254me1DEr245581Kc`
  * `hxxp[://]lkep[.]charitablemere[.]co[.]uk/3863907OZ17602479JA694127584qy8254tL1AYu245581qj`
* **Root Domain (Defanged):** `charitablemere[.]co[.]uk`

### C) File (Attachment) Artifacts
=============================================
* **File Name:** N/A
* **File Hash (SHA256):** N/A


## SECTION 2: Artifact Analysis
##############################
* **VirusTotal (IP Check):** (https://www.virustotal.com/gui/ip-address/213.254.170.16/detection)
* **AbuseIPDB:** (https://www.abuseipdb.com/check/213.254.170.16)
* **UrlScan.io:** (fzrd.charitablemere.co.uk - urlscan.io 
lkep.charitablemere.co.uk - urlscan.io)
* **CentralOps (Domain Lookup):** `charitablemere.co.uk` registered and valid until Feb 3, 2027.


## SECTION 3: Suggested Defensive Measures
#######################################

* **Declaration:** **True Positive – No Impact (Non-Issue)**
  *(Confirmed malicious/unwanted email; no user interaction, no device or account compromise. No incident response required beyond blocking.)*

* **Block the sending address:** `hqhxmikwxezmqnc[@]charitablemere[.]co[.]uk`
* **Block the Root Domain:** `charitablemere[.]co[.]uk`
* **Block The IP:** N/A *(IP blocking not recommended as it may belong to a shared Turkish hosting provider, risking false positives for legitimate traffic).*

***
**Disclaimer:** *This ticket is based on a real-world phishing sample analyzed within a controlled lab environment for educational and portfolio demonstration purposes.*
