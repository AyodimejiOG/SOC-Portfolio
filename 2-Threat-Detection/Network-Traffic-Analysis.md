# Network Traffic Analysis – Suspicious Outbound Communication  
*TryHackMe – SOC Analyst Level 1*

---

## Executive Summary

An alert identified abnormal outbound traffic from an internal host to an external IP address over an uncommon port. The traffic pattern suggested potential command-and-control (C2) communication.

A detailed network log analysis was conducted to determine legitimacy and impact.

Severity Assessment: **Medium–High**

---

## Alert Context

- Detection Source: Network monitoring tool
- Internal Host: Standard workstation
- External IP: Unknown / Untrusted
- Destination Port: Non-standard application port
- Traffic Pattern: Repeated beaconing intervals

---

## Investigation Process

### 1. Traffic Pattern Review

Analysis revealed:

- Consistent outbound requests every 60 seconds
- Small, uniform packet sizes
- Minimal inbound response data

This behaviour is consistent with beaconing communication.

---

### 2. Domain & IP Reputation Check

The external IP:

- Not associated with known vendors
- Recently registered domain
- Low reputation score

Geolocation inconsistent with business operations.

---

### 3. Endpoint Correlation

Cross-referenced:

- Endpoint process logs
- DNS resolution logs
- User login sessions

Findings:

- PowerShell process active during beaconing
- DNS query matched suspicious domain
- No legitimate application linked to traffic

---

## Indicators of Compromise (IOCs)

- Periodic outbound beaconing
- Non-standard port communication
- Suspicious DNS resolution
- Correlated endpoint scripting activity

---

## Threat Assessment

Activity strongly resembles:

- Command-and-control (C2) beacon
- Post-exploitation persistence
- Remote attacker communication

---

## Risk Assessment

If confirmed malicious, risks include:

- Remote attacker control
- Data exfiltration
- Network reconnaissance
- Malware propagation

Given correlated endpoint activity, risk assessed as **High**.

---

## Containment & Mitigation

- Isolated affected host
- Blocked external IP at firewall
- Conducted forensic image collection (simulated lab)
- Reviewed lateral movement logs
- Implemented enhanced monitoring

---

## Lessons Learned

Network behaviour analysis is critical in detecting threats that bypass signature-based detection. Repetitive beaconing patterns are strong indicators of C2 communication.

---

## Personal Reflection

This lab strengthened my ability to think across multiple log sources — network, DNS, and endpoint telemetry. It reinforced that effective threat detection requires correlation across systems, not isolated analysis.

It improved my confidence in identifying suspicious outbound traffic and understanding attacker persistence techniques.
