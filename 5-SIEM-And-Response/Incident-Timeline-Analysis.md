# Incident Timeline Analysis

## Overview

During a security investigation, analysts must understand the sequence of events that occurred during an attack. Building an incident timeline helps reconstruct attacker activity and identify how the compromise developed.

Timeline analysis is an essential skill for incident response teams.

---

## Collecting Investigation Data

To build a timeline, analysts gather information from multiple sources including:

- authentication logs
- endpoint logs
- network traffic logs
- SIEM alerts

Combining these data sources provides a clearer picture of attacker behaviour.

---

## Example Investigation Timeline

Example reconstructed timeline:

10:01 Multiple failed login attempts detected  
10:03 Successful login from external IP  
10:05 PowerShell command executed  
10:07 Outbound connection to suspicious server  

This sequence suggests that the attacker successfully authenticated and began executing commands on the compromised system.

---

## Importance of Timeline Reconstruction

Timeline analysis helps security teams:

- understand how the attacker gained access
- identify affected systems
- determine the scope of compromise
- guide containment and remediation efforts

Clear timelines also assist with incident reporting.

---

## Analyst Takeaway

Reconstructing attack timelines allows SOC analysts to understand the full scope of a security incident. This skill is critical for effective investigation and response.
