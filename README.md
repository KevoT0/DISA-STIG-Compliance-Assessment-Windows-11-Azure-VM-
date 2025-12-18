# DISA-STIG-Compliance-Assessment-Windows-11-Azure-VM-

# DISA STIG Compliance Assessment – Windows 11 (Azure VM)

## Overview
This project demonstrates a **DISA STIG (Security Technical Implementation Guide) compliance assessment** performed against a Windows 11 virtual machine hosted in Microsoft Azure. The objective was to evaluate system security posture against official **DISA Microsoft Windows 11 STIG v2r4** benchmarks using Tenable Nessus.

The system was **intentionally misconfigured** to trigger STIG findings and validate compliance detection, audit results, and reporting.

---

## Objectives
- Deploy a Windows 11 VM in Microsoft Azure  
- Intentionally weaken host security controls  
- Configure authenticated compliance scanning  
- Run a DISA STIG compliance audit using Nessus  
- Analyze failed, warning, and passed STIG controls  
- Identify high-risk configuration violations  

---

## Environment & Tools
- **Cloud Provider:** Microsoft Azure  
- **Operating System:** Windows 11 Pro (x64)  
- **Scanner:** Tenable Vulnerability Management (Nessus)  
- **Scan Type:** Advanced Network Scan + Compliance Audit  
- **Compliance Standard:** DISA Microsoft Windows 11 STIG v2r4  
- **Access Method:** RDP  

---

## Architecture & Setup
- Windows 11 VM deployed in Azure with a public IP  
- RDP enabled for administrative access  
- VM placed inside a custom VNet and subnet  
- Authenticated scanning enabled using local admin credentials  

<p align="center">
  <img src="images/stig-architecture.png" alt="STIG Lab Architecture" width="800">
</p>

---

## Step 1: Azure VM Deployment
A Windows 11 Pro virtual machine was created in Azure and validated for connectivity via RDP.

<p align="center">
  <img src="images/stig-vm-deployment.png" width="700">
</p>

---

## Step 2: Intentional Security Misconfiguration
To validate STIG findings, multiple **non-compliant configurations** were deliberately introduced.

### Host-Level Weakening
- Windows Defender Firewall disabled
- Password policies weakened
- Account controls misconfigured

<p align="center">
  <img src="images/firewall-disabled.png" width="700">
</p>

---

## Step 3: User & Privilege Misconfiguration (Critical)
The following **high-risk STIG violations** were intentionally introduced:

- Built-in **Guest account enabled**
- Guest account **added to Administrators group**
- Guest account **not renamed**
- Password expiration and complexity policies disabled

<p align="center">
  <img src="images/guest-admin.png" width="800">
</p>

---

## Step 4: Nessus Scan Configuration
An **Advanced Network Scan** was configured with:

- Full discovery (ICMP, TCP, SYN)
- Authenticated Windows credentials
- Remote Registry enabled
- Administrative shares enabled
- Server service enabled

<p align="center">
  <img src="images/nessus-advanced-scan.png" width="800">
</p>

---

## Step 5: DISA STIG Compliance Selection
The **DISA Microsoft Windows 11 STIG v2r4** compliance audit was added to the scan.

<p align="center">
  <img src="images/stig-selection.png" width="800">
</p>

---

## Step 6: Scan Execution
The scan was executed on-demand against the internal VM IP address and completed successfully.

<p align="center">
  <img src="images/stig-scan-running.png" width="700">
</p>

---

## Scan Results Summary

### Vulnerabilities by Severity
- **Critical:** 0  
- **High:** 3  
- **Medium:** 4  
- **Low:** 2  

<p align="center">
  <img src="images/vuln-summary.png" width="700">
</p>

---

### STIG Compliance Results
Out of **259 total STIG checks**:

- **149 Failed**
- **13 Warning**
- **97 Passed**

<p align="center">
  <img src="images/stig-overview.png" width="800">
</p>

---

## Notable STIG Failures

### Guest Account Violations (Critical)
The scan correctly identified the following failures:

- **WN11-SO-000025** – Built-in guest account must be renamed  
- **WN11-SO-000010** – Built-in guest account must be disabled  

<p align="center">
  <img src="images/guest-stig-failure.png" width="800">
</p>

---

### Password & Authentication Failures
Multiple authentication-related STIGs failed due to intentional misconfiguration:

- Password expiration not enforced  
- Minimum password length not met  
- Password history not configured  
- Password complexity disabled  
- RDP password prompts not enforced  

<p align="center">
  <img src="images/password-stig-failures.png" width="800">
</p>

---

## Key Takeaways
- DISA STIGs focus on **secure configuration**, not just vulnerabilities  
- Authenticated scans are mandatory for accurate compliance assessment  
- Misconfigured accounts introduce severe security risk  
- STIG audits provide measurable, policy-driven security posture  
- Cloud-hosted systems are still fully subject to compliance standards  

---

## Skills Demonstrated
- Azure Windows VM deployment  
- Windows local security policy management  
- Account and privilege hardening analysis  
- Tenable Nessus advanced scan configuration  
- DISA STIG compliance auditing  
- Security baseline validation  
- GRC / compliance assessment methodology  

---

## Next Steps
- Remediate failed STIG controls  
- Disable and secure guest accounts  
- Enforce password and authentication policies  
- Re-run compliance scan to validate remediation  
- Export compliance reports for audit evidence  

---

## Disclaimer
This project was conducted in a controlled lab environment for educational and portfolio purposes only.
