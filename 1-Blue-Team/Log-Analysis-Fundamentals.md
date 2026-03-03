# Log Analysis Fundamentals  
*TryHackMe – SOC Analyst Level 1*

## Overview

This lab focused on one of the most important skills for a SOC Analyst — log analysis. Logs provide visibility into system and network activity, and they are often the first source of evidence during an investigation.

Through this lab, I learned how to interpret log entries, identify suspicious patterns, and differentiate between normal and abnormal behaviour.

---

## Objectives

- Understand what logs are and why they matter
- Learn different types of logs
- Identify suspicious indicators in log data
- Develop basic log investigation skills

---

## Types of Logs Covered

### 1. Authentication Logs
Used to track:
- Successful logins
- Failed login attempts
- Remote access activity

Repeated failed login attempts may indicate brute-force attacks.

### 2. System Logs
Provide insight into:
- System errors
- Service failures
- Privilege changes

### 3. Network Logs
Used to detect:
- Unusual outbound connections
- Suspicious IP addresses
- Data exfiltration attempts

---

## Key Concepts Learned

### Log Correlation
Single log entries may not indicate an attack. However, when multiple suspicious events occur within a short timeframe, they can reveal malicious activity.

### Indicators of Compromise (IOCs)
Examples include:
- Unknown IP addresses
- Abnormal login times
- Multiple failed authentication attempts
- Unexpected administrative access

---

## Practical Takeaways

This lab helped me understand that log analysis requires patience and attention to detail. Even small anomalies can indicate a larger security issue.

I also realised the importance of:
- Pattern recognition
- Understanding normal system behaviour
- Documenting findings clearly

---

## Reflection

Log analysis is a core responsibility of a Tier 1 SOC Analyst. This lab improved my confidence in reading and interpreting security logs and strengthened my analytical mindset.

It reinforced the idea that cybersecurity is investigative work — every log tells a story.
