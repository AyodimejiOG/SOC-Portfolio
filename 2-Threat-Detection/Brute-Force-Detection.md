# Brute Force Attack Detection – Authentication Log Analysis  
*TryHackMe – SOC Analyst Level 1*

---

## Executive Summary

An alert was triggered due to multiple failed authentication attempts against a user account within a short timeframe. The pattern suggested a potential brute-force attack targeting remote access services.

A structured log analysis was performed to validate the threat, assess impact, and determine whether account compromise occurred.

Severity Assessment: **Medium–High**  
Compromise Confirmed: **No (based on available logs)**

---

## Alert Context

- Detection Source: SIEM correlation rule
- Trigger Condition: Excessive failed login attempts
- Target Account: Standard user account
- Service Targeted: SSH / Remote authentication service

Threshold exceeded: 15+ failed attempts within 2 minutes.

---

## Investigation Process

### 1. Authentication Log Analysis

I reviewed authentication logs focusing on:

- Timestamp patterns
- Source IP address
- Username targeting
- Authentication method used

Findings:

- Rapid, sequential failed attempts
- All attempts originated from a single external IP
- Username remained consistent across attempts
- Attempts occurred outside normal working hours

The pattern demonstrated automated behaviour rather than manual login error.

---

### 2. Source IP Investigation

The attacking IP address was analysed for:

- Geolocation
- Reputation
- Historical malicious activity

Findings:

- Originated from a foreign region not associated with business operations
- Associated with previous brute-force attempts (based on threat intelligence)
- Hosted on a VPS provider commonly abused for attacks

Assessment: Likely malicious automated scanner or botnet activity.

---

### 3. Success Attempt Correlation

After failed attempts, I reviewed logs for:

- Any successful login events
- MFA challenge logs
- Privilege escalation activity
- Suspicious post-authentication behaviour

Findings:

- No successful authentication recorded
- No anomalous activity detected
- No session tokens generated

Conclusion: Attack unsuccessful.

---

## Indicators of Compromise (IOCs)

- High-volume failed logins
- Rapid request interval (automation pattern)
- Single-source IP concentration
- Out-of-hours targeting
- No legitimate user behaviour correlation

---

## Threat Analysis

This activity aligns with credential brute-force attempts where attackers attempt password guessing through automation.

Primary Objectives of Such Attacks:

- Account compromise
- Privilege escalation
- Lateral movement
- Persistence establishment

---

## Risk Assessment

Although unsuccessful, brute-force attacks pose risk because:

- Weak passwords may eventually be guessed
- Repeated attempts increase account lockout risks
- Attackers may pivot to password spraying

Potential Business Impact (if successful):

- Remote access compromise
- Data exposure
- Internal reconnaissance

---

## Containment & Mitigation

- Source IP blocked at firewall
- Account lockout policy reviewed
- MFA enforcement validated
- Alert threshold fine-tuned
- Monitoring enabled for similar patterns

---

## Lessons Learned

This investigation reinforced:

- The importance of correlation rules in detecting automation
- The need for strong authentication controls
- The value of analysing behavioural patterns, not just event counts

---

## Personal Reflection

This case strengthened my ability to analyse authentication logs systematically. Rather than reacting to volume alone, I evaluated behaviour, intent, and impact before determining severity.

It reinforced how Tier 1 analysts must distinguish between normal user mistakes and structured attack attempts.
