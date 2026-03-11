# Linux Privilege Escalation Detection

## Overview

Privilege escalation is a common technique used by attackers after gaining initial access to a system. By escalating privileges, an attacker can move from a low-privileged account to a root or administrative account, allowing them to take full control of the system.

In this lab, I investigated how privilege escalation attempts can be detected on Linux systems by analysing logs and monitoring user activity.

---

## Initial Access Scenario

Attackers often begin with limited user access obtained through stolen credentials, weak passwords, or exposed services such as SSH.

Example login log:

Failed password for user john from 185.25.90.11 port 44522 ssh2

Multiple failed login attempts followed by a successful login can indicate credential brute-forcing or password guessing.

---

## Indicators of Privilege Escalation

After gaining access, attackers attempt to elevate privileges using various methods.

Common indicators include:

- Unexpected use of `sudo`
- Execution of administrative commands by non-admin users
- Creation of new privileged accounts
- Access to sensitive system files

Example log entry:

sudo: john : TTY=pts/1 ; COMMAND=/bin/bash

This indicates that the user attempted to run a command with elevated privileges.

---

## Investigating Suspicious Commands

Analysts should examine command history and authentication logs to determine whether privileged commands were legitimate.

Commands often associated with privilege escalation include:

- sudo su
- chmod +s
- modifying `/etc/sudoers`
- accessing `/etc/shadow`

These commands may allow attackers to gain permanent elevated access.

---

## Detection Techniques

SOC analysts detect privilege escalation by monitoring:

- authentication logs
- unusual sudo activity
- abnormal command execution
- changes to system permissions

Security monitoring tools and SIEM platforms can generate alerts when privileged commands are executed unexpectedly.

---

## Analyst Takeaway

Privilege escalation detection is critical in preventing attackers from gaining full control of systems.

Through this investigation I strengthened my ability to:

- analyse Linux authentication logs
- identify suspicious sudo activity
- recognise common privilege escalation techniques
- understand attacker behaviour after initial compromise
