# SSH Brute Force Investigation

## Overview

Secure Shell (SSH) is widely used to remotely access Linux systems. Because of its importance in system administration, it is also a frequent target for attackers attempting to gain unauthorized access.

One of the most common attack techniques against SSH services is a brute force attack, where attackers repeatedly attempt to guess login credentials.

This lab focused on detecting SSH brute force attacks through log analysis.

---

## SSH Authentication Logs

SSH activity is typically recorded in:

```
/var/log/auth.log
```

This log contains records of both successful and failed login attempts.

Example failed login:

```
Failed password for invalid user admin from 192.168.1.50 port 43322 ssh2
```

Repeated entries like this often indicate automated attack attempts.

---

## Indicators of Brute Force Attacks

SOC analysts should look for patterns such as:

- repeated login failures
- attempts targeting multiple usernames
- login attempts from unfamiliar IP addresses
- high frequency of login attempts within a short time period

Example pattern:

```
Failed password for root from 185.244.25.34
Failed password for admin from 185.244.25.34
Failed password for test from 185.244.25.34
```

This suggests an attacker trying different usernames.

---

## Successful Login After Failures

A successful login following many failed attempts may indicate that an attacker successfully guessed the password.

Example:

```
Accepted password for root from 185.244.25.34 port 50122 ssh2
```

This should trigger immediate investigation.

---

## Analyst Takeaway

SSH brute force attacks are extremely common across internet-facing systems. Monitoring authentication logs allows SOC analysts to detect these attacks early.

Through this lab I strengthened my ability to:

- analyse SSH authentication logs
- detect brute force patterns
- investigate suspicious login behaviour
- identify potential unauthorized access
