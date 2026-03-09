# Suspicious PowerShell Activity – Endpoint Investigation  
*TryHackMe – SOC Analyst Level 1*

---

## Executive Summary

An endpoint detection alert flagged unusual PowerShell execution with encoded command-line arguments. This behaviour is commonly associated with malware execution and post-exploitation activity.

The objective was to determine whether this activity was malicious or legitimate administrative usage.

Severity Assessment: **High (based on behaviour pattern)**

---

## Alert Context

- Detection Source: EDR telemetry
- Process: powershell.exe
- Command-line flag: EncodedCommand
- Parent process: Unusual application execution chain

Encoded commands often indicate obfuscation attempts.

---

## Investigation Process

### 1. Command-Line Analysis

The encoded PowerShell command was:

- Extracted from logs
- Decoded using Base64 decoding
- Reviewed for suspicious functions

Decoded script behaviour included:

- Remote URL request
- File download
- Execution of downloaded payload

This pattern strongly indicates malicious staging behaviour.

---

### 2. Process Tree Examination

I analysed the parent-child relationship:

- Parent process was a document viewer application
- PowerShell spawned unexpectedly
- Subsequent child process executed temporary file

This chain suggested macro-based or document-delivered malware.

---

### 3. Network Activity Review

Reviewed:

- Outbound HTTP connections
- DNS resolution logs
- Proxy logs

Findings:

- Connection to newly registered domain
- No business justification for connection
- Short-lived C2-style communication pattern

---

## Indicators of Compromise (IOCs)

- Encoded PowerShell execution
- Suspicious parent-child process chain
- Remote payload retrieval
- Newly registered command-and-control domain

---

## Threat Classification

Activity resembles:

- Initial access via phishing attachment
- Malware staging via PowerShell
- Possible remote access trojan (RAT) behaviour

---

## Risk Assessment

If left undetected, potential impact:

- Persistence establishment
- Credential harvesting
- Lateral movement
- Data exfiltration

Given execution behaviour, risk assessed as **High**.

---

## Containment & Remediation

- Endpoint isolated from network
- Malicious file hash submitted to threat intelligence
- Domain blocked at proxy/firewall
- Full system scan initiated
- User credentials reset as precaution

---

## Lessons Learned

PowerShell remains a powerful but frequently abused administrative tool. Behavioural analysis (process relationships and command-line review) is critical in detecting abuse.

---

## Personal Reflection

This investigation deepened my understanding of endpoint telemetry and process analysis. It reinforced the importance of reviewing execution context, not just process names.

As a SOC Analyst, identifying suspicious behaviour chains is key to early malware detection.
