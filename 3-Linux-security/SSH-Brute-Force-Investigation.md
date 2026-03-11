# SSH Brute Force Investigation

## Overview

Secure Shell (SSH) is widely used for remote administration of Linux systems. Because of its importance, attackers frequently target SSH services using brute force attacks in an attempt to guess valid credentials.

This lab focused on identifying SSH brute force activity using Linux authentication logs.

---

## Understanding Brute Force Attacks

A brute force attack involves repeatedly attempting different username and password combinations until valid credentials are discovered.

These attacks often originate from automated scripts or botnets scanning large numbers of systems.

---

## Log Evidence

Authentication logs provide clear evidence of brute force attempts.

Example log entries:

Failed password for invalid user admin from 45.77.23.19 port 55212 ssh2  
Failed password for invalid user admin from 45.77.23.19 port 55218 ssh2  
Failed password for invalid user admin from 45.77.23.19 port 55221 ssh2

Repeated login attempts from the same IP address within a short time period strongly indicate automated credential attacks.

---

## Investigative Approach

During the investigation I focused on identifying:

- the attacking IP address
- the number of failed login attempts
- targeted usernames
- whether a successful login occurred

Analysts must determine whether the attack resulted in account compromise.

---

## Defensive Measures

Common defensive measures against SSH brute force attacks include:

- implementing strong password policies
- enabling multi-factor authentication
- restricting SSH access using firewall rules
- using intrusion prevention tools such as Fail2Ban

These controls reduce the risk of successful credential attacks.

---

## Analyst Takeaway

SSH brute force activity is one of the most common attack patterns observed on internet-facing systems. SOC analysts must be able to quickly recognise these patterns and determine whether a compromise has occurred.
