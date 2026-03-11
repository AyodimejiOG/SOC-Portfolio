# Linux Privilege Escalation Detection

## Overview

Privilege escalation is a common technique used by attackers after gaining initial access to a system. The goal is to move from a low-privileged user account to a more powerful account, often root, which allows full control over the system.

Detecting privilege escalation attempts is an important responsibility for SOC analysts because it often indicates that an attacker has already compromised a machine.

This lab focused on identifying suspicious privilege escalation activity using Linux logs and system monitoring.

---

## What is Privilege Escalation?

Privilege escalation occurs when a user gains higher permissions than originally intended.

Two common types include:

### Vertical Privilege Escalation
A user gains higher permissions than their original account.

Example:
```
user → root
```

### Horizontal Privilege Escalation
A user accesses resources belonging to another user at the same privilege level.

---

## Monitoring sudo Usage

One of the most common indicators of privilege escalation attempts is unusual use of the `sudo` command.

Relevant log location:

```
/var/log/auth.log
```

Example log entry:

```
sudo: john : TTY=pts/0 ; COMMAND=/bin/bash
```

This indicates that the user **john** executed a command with elevated privileges.

Analysts should investigate when:

- unexpected users run sudo commands
- multiple sudo attempts occur
- administrative commands run outside normal working hours

---

## Suspicious Indicators

Possible indicators of privilege escalation include:

- multiple failed sudo attempts
- execution of sensitive system commands
- creation of new privileged accounts
- modification of system files

Important files to monitor:

```
/etc/passwd
/etc/shadow
/etc/sudoers
```

Unauthorized changes to these files may indicate compromise.

---

## Analyst Takeaway

Privilege escalation is a key stage in many attack chains. By monitoring authentication logs and administrative command usage, SOC analysts can identify suspicious activity early.

This lab improved my understanding of:

- how privilege escalation appears in Linux logs
- monitoring sudo activity
- identifying suspicious administrative behaviour
- recognising indicators of system compromise
