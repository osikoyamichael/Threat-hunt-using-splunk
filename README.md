# Threat-hunt-using-splunk Detecting Adversary Reconnaissance

## Overview

This project simulates a proactive threat hunt based on a law enforcement advisory. Using the BOTSv2 (Boss of the SOC) dataset within Splunk, I identified an adversary conducting stealthy reconnaissance using a non-standard browser (Naenara) over port 80. To validate the threat, I integrated IPinfo for geographic and ASN enrichment, moving the investigation from a suspicious log entry to actionable threat intelligence.

## 📖 The Scenario
Intelligence Input: Law enforcement warned of a campaign targeting our industry. The adversary is conducting reconnaissance on public-facing web servers using a non-standard browser over port 80 to bypass traditional signature-based detection.

## Tech stack & Lab Environment 
- SIEM: splunk
- Dataset: BOTSV2
- Enrichment: ipinfo and whatismybrower (for geographical and useragent infomation)
-  Environment: Window
-  Analysis Focus: IP Geographical, user-agent, ASN Reputation

  ## Threat hunt logic
  - Identify unusual http_user_agent mostly on the rare string.(Mozilla/5.0 (X11; U; Linux i686; ko-KP; rv: 19.1br) Gecko/20130508 Fedora/1.9.1-2.5.rs3.0 NaenaraBrowser/3.5b4") 
  - Get the source IP address of the  user_agent and check the geographical location if the business operate in that region.
  - Check the activities, url_path , http method(GET and POST )

  ## MITRE ATT&CK Mapping
- TA0007 – Discovery
- TA0009 – Collection
- T1213 – Data from Information Repositories
- T1592 – Gather Victim Identity Information
## Key Findings
- Sensitive file /files/company_contacts.xlsx was publicly accessible
- External entity successfully downloaded internal contact database
- Suspicious user-agent indicated attempted obfuscation
- Activity aligned with early-stage reconnaissance tactics

## Mitigation & Strategic Outcomes
- Removed public access to sensitive internal files (/files/company_contacts.xlsx)
- Enforced authentication and access controls
- Implentation of WAF(to detect and  block suscipous user agent)
- Encrypt file at rest and transit(TLS)
- Conducted phishing awareness training
- Alerted employees about possible targeted attacks
- Simulated phishing campaigns to test readiness
