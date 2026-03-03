# Phishing Email Investigation – Credential Harvesting Attempt  
*TryHackMe – SOC Analyst Level 1*

---

## Executive Summary

A suspicious email alert was triggered by the email security gateway due to abnormal sender reputation and embedded URL characteristics. 

Initial review suggested a potential credential harvesting attempt targeting internal users. A structured investigation was conducted to validate the threat, identify indicators of compromise (IOCs), and determine risk exposure.

The email was confirmed to be a phishing attempt designed to mimic a legitimate service and capture user login credentials.

Severity Assessment: **High (if interacted with)**  
User Interaction Confirmed: **No** (based on available telemetry)

---

## Alert Context

- Alert Source: Email Security Gateway  
- Detection Type: Suspicious URL + Domain Reputation  
- Targeted User: Standard business user account  
- Email Theme: Account verification / urgent security notice  

The tone of the message created urgency and implied account suspension if no action was taken — a common social engineering tactic.

---

## Investigation Process

### 1. Sender Analysis

The sender display name impersonated a legitimate brand; however:

- The sender domain slightly differed from the official domain (character substitution).
- SPF and DKIM authentication checks failed.
- The sending IP address was not associated with the legitimate organisation.

This strongly indicated domain spoofing.

**Assessment:** High likelihood of impersonation attempt.

---

### 2. Header Examination

Full header analysis revealed:

- Return-Path mismatch
- Mail relay through an unrelated hosting provider
- Recently registered sending domain (based on threat intelligence lookup)

The short domain age increased suspicion of malicious intent.

**Assessment:** Infrastructure consistent with phishing campaigns.

---

### 3. URL & Landing Page Analysis

The embedded hyperlink:

- Displayed a legitimate-looking URL in text
- Redirected to a different domain when hovered
- Used HTTPS but with a generic certificate

The landing page:

- Closely resembled a known login portal
- Requested credentials immediately
- Had no additional navigation options (typical phishing indicator)

No backend validation mechanisms were present — suggesting the sole purpose was credential harvesting.

**Assessment:** Confirmed credential harvesting page.

---

### 4. Endpoint & User Activity Review

To determine impact, I reviewed:

- Email click logs
- Proxy logs
- Authentication logs for unusual login attempts
- MFA logs

Findings:
- No evidence of link click from the targeted user
- No suspicious login attempts post-delivery
- No anomalous authentication behaviour

**Conclusion:** No successful compromise detected.

---

## Indicators of Compromise (IOCs)

- Spoofed domain with minor character variation
- Recently registered domain
- Failed SPF/DKIM validation
- URL redirect mismatch
- Credential harvesting page design pattern

---

## Threat Classification

Mapped to common phishing attack patterns involving:

- Brand impersonation
- Urgency-based manipulation
- Credential harvesting
- Infrastructure designed for short-term use

Primary Objective: Account compromise for potential lateral movement or data access.

---

## Risk Assessment

If successful, potential impact could include:

- Compromised corporate credentials
- Privilege escalation
- Business email compromise (BEC)
- Data exfiltration
- Internal phishing propagation

Although no interaction occurred, the attack demonstrated realistic deception techniques.

---

## Containment & Remediation Actions

- Malicious domain blocked at email gateway
- Domain added to organisation blocklist
- Threat intelligence platform updated
- Awareness reminder issued to affected department
- Monitoring enabled for related domain variants

---

## Lessons Learned

This investigation reinforced several key insights:

- Phishing attacks rely heavily on psychological manipulation, not just technical evasion.
- Domain similarity attacks remain highly effective.
- Email authentication failures (SPF/DKIM) are strong early indicators.
- Rapid triage prevents escalation into credential compromise.

---

## Personal Reflection

This lab strengthened my confidence in structured phishing investigations. Rather than simply identifying a suspicious email, I followed a methodical approach:

1. Validate the sender
2. Analyse infrastructure
3. Inspect the payload
4. Check user impact
5. Assess business risk

It highlighted the importance of thinking beyond the alert itself and considering potential downstream impact.

As a future Tier 1 SOC Analyst, this type of structured analysis ensures accurate triage, reduced false positives, and effective escalation when required.

---

*Investigation completed as part of SOC Analyst Level 1 training on TryHackMe.*
