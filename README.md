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
  - T1592: Gather Victim Host Information	Reconnaissance
  - T1071.001:	Application Layer Protocol: Web Protocols	Command & Control
  - T1589:	Gather Victim Identity Information	Reconnaissance

## 🏆 Key Achievements & Strategic Outcomes

- Intelligence-Led Defense: Successfully converted a generic law enforcement advisory into a specific, actionable hunting query, reducing the time from "threat awareness" to "threat detection."

- Attack Surface Visibility: Identified 100% of the non-standard browser traffic targeting the (www.froth.ly) infrastructure, uncovering reconnaissance activity that bypassed traditional signature-based IDS.

- Operational Efficiency: Integrated the IPinfo API to automate geographic and ASN enrichment. This reduced the investigation time (MTTI) per IP from several minutes of manual lookup to near-instant results.

- Proactive Mitigation: Developed a custom Correlation Search in Splunk to alert the SOC team in real-time when "Long Tail" User-Agents are detected on sensitive web assets.

- False Positive Reduction: Utilized statistical analysis (the "Power of the Outlier") to distinguish between legitimate automated bots and targeted adversary reconnaissance.
