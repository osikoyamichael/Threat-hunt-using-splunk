## 🚨 SOC Alert: Unauthorized Access to Sensitive Contact File

### **Alert Title**

Suspicious External Download of Company Contact Database

---

### **Severity**

🔴 High

---

### **Date/Time Detected**

2017-08-05 08:15:48 UTC

---

### **Alert Description**

A successful HTTP GET request was observed from an external IP address (`85.203.47.86`) targeting a sensitive internal file:

```
/files/company_contacts.xlsx
```

The file appears to contain company contact information and was downloaded successfully (`HTTP 200`). The request originated from a suspicious user agent associated with a North Korean browser profile, indicating potential malicious reconnaissance activity.

---

### **Log Evidence**

* **Source IP:** 85.203.47.86
* **HTTP Method:** GET
* **Requested Resource:** /files/company_contacts.xlsx
* **HTTP Status:** 200 (Success)
* **Content Type:** application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
* **User Agent:** Mozilla/5.0 (X11; U; Linux i686; ko-KP; rv: 19.1br) Gecko/20130508 Fedora/1.9.1-2.5.rs3.0 NaenaraBrowser/3.5b4"
* **Referrer:** [http://www.froth.ly/](http://www.froth.ly/)
* **Server:** Apache/2.2.15 (CentOS)

---

### **Analysis**

This activity indicates that an external entity successfully accessed and downloaded a file containing internal company contacts. This type of data is highly valuable for adversaries and is commonly used in the reconnaissance phase of cyber attacks.

Key concerns:

* Exposure of employee names, emails, and possibly roles
* Use of suspicious user-agent string suggesting possible threat actor obfuscation

The presence of a public-facing file path (`/files/`) suggests a possible misconfiguration in access control, allowing unauthorized download of sensitive data.

---

### **Threat Context**

The stolen contact data can be leveraged for:

* 🎯 **Spear Phishing Attacks**
  Highly targeted emails crafted using real employee data

* 💰 **Business Email Compromise (BEC)**
  Impersonation of executives or finance personnel for fraud

* 🧠 **Social Engineering**
  Manipulating employees using insider knowledge

* 🔑 **Credential Harvesting**
  Fake login portals targeting known users

* 🦠 **Malware Delivery**
  Sending malicious attachments to trusted contacts

This behavior aligns with **initial reconnaissance and data staging** in the cyber kill chain.

---

### **MITRE ATT&CK Mapping**

* **TA0007 – Discovery**
* **TA0009 – Collection**
* **T1213 – Data from Information Repositories**
* **T1592 – Gather Victim Identity Information**

---

### **Impact Assessment**

* Exposure of internal company contact database
* Increased risk of targeted phishing campaigns
* Potential financial fraud via BEC
* Elevated likelihood of follow-on attacks

---

### **Recommended Actions**

#### Immediate:

* 🔒 Remove or restrict public access to `/files/company_contacts.xlsx`
* 🔍 Search for additional access attempts to sensitive files
* 📢 Notify affected users of potential phishing risk

#### Short-Term:

* 🛡️ Implement authentication for sensitive file access
* 📊 Monitor email systems for anomalies (spoofing, unusual logins)
* 🌐 Investigate source IP reputation and related activity

 Long-Term:
- Enforce proper access control and data classification policies
- Conduct security awareness training (phishing, social engineering)
-  Deploy DLP (Data Loss Prevention) solutions
- Improve logging and alerting for file access events

---

### **Conclusion**

This alert represents a **high-confidence reconnaissance event** involving unauthorized access to sensitive internal data(company conatact ) . Immediate containment and user awareness measures are critical to prevent escalation into phishing, credential compromise, or financial fraud incidents.

