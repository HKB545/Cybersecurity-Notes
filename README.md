# Cybersecurity Learning Notes and Security Architecture

A centralized cybersecurity knowledge repository covering foundational security principles, network defense concepts, threat analysis, Linux hardening techniques, security tooling, and structured career development pathways.

This repository is designed to serve as a long-term reference for students, aspiring security professionals, system administrators, and cybersecurity practitioners seeking a structured approach to security education and operational understanding.

---

# Table of Contents

* [Overview](#overview)
* [The CIA Triad](#the-cia-triad)
* [Essential Security Networking Concepts](#essential-security-networking-concepts)
* [Common Cyber Attacks and Threat Vectors](#common-cyber-attacks-and-threat-vectors)
* [Linux Security Basics and System Hardening](#linux-security-basics-and-system-hardening)
* [Security Tools Overview Matrix](#security-tools-overview-matrix)
* [Structured Cybersecurity Learning Roadmap](#structured-cybersecurity-learning-roadmap)
* [Recommended Learning Strategy](#recommended-learning-strategy)
* [Future Topics](#future-topics)

---

# Overview

Cybersecurity is built upon a combination of technical controls, defensive strategies, secure system configurations, and continuous risk management practices.

This repository documents essential concepts required for understanding:

* Information Security
* Network Security
* Linux Security
* Threat Detection
* Vulnerability Management
* Penetration Testing
* Security Operations
* Security Architecture

The objective is to establish a strong foundation before progressing into advanced offensive or defensive security disciplines.

---

# The CIA Triad

The CIA Triad forms the foundation of modern information security.

Every security control, policy, monitoring solution, and risk management framework is designed to protect one or more of these principles:

1. Confidentiality
2. Integrity
3. Availability

---

## Confidentiality

Confidentiality ensures that sensitive information is accessible only to authorized users and systems.

### Security Controls

* AES-256 Encryption
* RSA Encryption
* Multi-Factor Authentication (MFA)
* Access Control Lists (ACLs)
* Role-Based Access Control (RBAC)

### Example Violation

A database breach exposing unencrypted customer credentials.

---

## Integrity

Integrity ensures information remains accurate, trustworthy, and unchanged throughout its lifecycle.

### Security Controls

* SHA-256 Hashing
* SHA-512 Hashing
* Digital Signatures
* File Integrity Monitoring
* Journaling File Systems

### Example Violation

A Man-in-the-Middle (MitM) attack modifying transaction details during transmission.

---

## Availability

Availability ensures systems, applications, and data remain accessible when required by authorized users.

### Security Controls

* High Availability Clusters
* Load Balancers
* Redundant Infrastructure
* Backup Solutions
* DDoS Mitigation Services

### Example Violation

A ransomware attack preventing access to critical business systems.

---

# Essential Security Networking Concepts

Understanding network security fundamentals is critical for defending modern infrastructure.

---

## Firewalls

Firewalls inspect, monitor, and control network traffic according to predefined security rules.

### Types of Firewalls

| Type                            | Description                                      |
| ------------------------------- | ------------------------------------------------ |
| Packet Filtering Firewall       | Filters traffic based on IP addresses and ports  |
| Stateful Firewall               | Tracks connection states                         |
| Proxy Firewall                  | Intermediary traffic inspection                  |
| Next-Generation Firewall (NGFW) | Deep packet inspection and application awareness |

---

## DMZ (Demilitarized Zone)

A DMZ is a segregated network segment that hosts public-facing services while protecting internal systems.

### Common DMZ Services

* Web Servers
* DNS Servers
* Mail Servers
* Reverse Proxies
* Public APIs

### Security Benefit

Compromise of a public-facing service does not automatically expose the internal network.

---

## Secure vs Insecure Protocols

Modern environments should replace legacy plaintext protocols with encrypted alternatives.

| Insecure Protocol | Secure Alternative | Default Port | Purpose                  |
| ----------------- | ------------------ | ------------ | ------------------------ |
| HTTP              | HTTPS              | 443          | Secure Web Communication |
| Telnet            | SSH                | 22           | Remote Administration    |
| FTP               | SFTP / SCP         | 22           | Secure File Transfer     |
| LDAP              | LDAPS              | 636          | Directory Authentication |

---

# Common Cyber Attacks and Threat Vectors

Understanding attack methodologies improves defensive capabilities and incident response readiness.

---

## Social Engineering and Phishing

Social engineering attacks exploit human psychology rather than technical vulnerabilities.

### Common Objectives

* Credential Theft
* Financial Fraud
* Malware Delivery
* Unauthorized Access

### Mitigation Strategies

* Security Awareness Training
* Email Filtering
* MFA Enforcement
* DMARC, DKIM, and SPF Implementation

---

## Malware and Ransomware

Malware refers to malicious software designed to damage, disrupt, or gain unauthorized access to systems.

Ransomware encrypts files and demands payment for decryption.

### Mitigation Strategies

* Endpoint Detection and Response (EDR)
* Application Control
* Least Privilege Enforcement
* Offline Backups
* Security Monitoring

---

## SQL Injection (SQLi)

SQL Injection occurs when unsanitized user input is interpreted as database commands.

### Potential Impact

* Authentication Bypass
* Data Theft
* Database Modification
* Complete Database Exposure

### Mitigation

* Parameterized Queries
* Prepared Statements
* Input Validation
* Least Privilege Database Accounts

---

## Cross-Site Scripting (XSS)

XSS allows attackers to inject malicious JavaScript into trusted web applications.

### Potential Impact

* Session Hijacking
* Credential Theft
* User Impersonation
* Client-Side Malware Execution

### Mitigation

* Output Encoding
* Input Validation
* Content Security Policy (CSP)
* Secure Cookie Configuration

---

# Linux Security Basics and System Hardening

Operating system hardening reduces attack surfaces and limits unauthorized access.

---

## SSH Hardening

Modify the SSH daemon configuration file:

```text
/etc/ssh/sshd_config
```

Recommended security settings:

```text
PermitRootLogin no

PasswordAuthentication no

AllowUsers security_analyst sec_ops
```

### Purpose

| Setting                   | Security Benefit                  |
| ------------------------- | --------------------------------- |
| PermitRootLogin no        | Prevents direct root access       |
| PasswordAuthentication no | Enforces key-based authentication |
| AllowUsers                | Restricts authorized SSH users    |

Apply configuration changes:

```bash
sudo systemctl restart sshd
```

---

## Authentication Log Monitoring

Monitoring authentication logs helps identify:

* Brute Force Attempts
* Unauthorized Access
* Failed Logins
* Privilege Escalation Activity

### Common Log Locations

| Distribution           | Log File            |
| ---------------------- | ------------------- |
| Debian / Ubuntu / Kali | `/var/log/auth.log` |
| CentOS / RHEL          | `/var/log/secure`   |

### Example

```bash
sudo grep "Failed password" /var/log/auth.log
```

---

# Security Tools Overview Matrix

Common security tools used across offensive and defensive security operations.

| Tool            | Domain              | Primary Purpose                  | Example Usage            |
| --------------- | ------------------- | -------------------------------- | ------------------------ |
| Nmap            | Reconnaissance      | Host Discovery and Port Scanning | `nmap -sV -sC target_ip` |
| Wireshark       | Network Analysis    | Packet Inspection                | GUI-Based Analysis       |
| Burp Suite      | Web Security        | Web Application Testing          | Intercepting Proxy       |
| Metasploit      | Penetration Testing | Exploit Validation               | `msfconsole`             |
| John the Ripper | Password Auditing   | Hash Cracking                    | `john hash.txt`          |
| Snort           | Network Defense     | Intrusion Detection              | Rule-Based Monitoring    |

---

# Structured Cybersecurity Learning Roadmap

A progressive path from foundational concepts to advanced cybersecurity specialization.

---

## Phase 1 — Core Foundations

### Focus Areas

* Networking Fundamentals
* Operating Systems
* Computer Hardware
* Linux Fundamentals

### Recommended Certifications

* CompTIA Network+
* LPIC-1
* Linux Essentials

---

## Phase 2 — Security Fundamentals

### Focus Areas

* Security Principles
* Threat Modeling
* Access Control
* Risk Management

### Recommended Certifications

* CompTIA Security+

---

## Phase 3 — Practical Security Operations

### Focus Areas

* Vulnerability Assessment
* Penetration Testing
* Network Analysis
* Security Monitoring

### Recommended Certifications

* eJPT
* CCNA

---

## Phase 4 — Advanced Specialization

### Focus Areas

* Red Team Operations
* Security Engineering
* Security Architecture
* Governance and Risk Management

### Recommended Certifications

* OSCP
* CISSP

---

# Recommended Learning Strategy

For long-term success:

1. Master networking before hacking tools.
2. Learn Linux administration thoroughly.
3. Build hands-on labs instead of relying solely on theory.
4. Practice consistently using virtual machines.
5. Document findings and projects publicly.
6. Focus on understanding concepts rather than memorizing commands.
7. Develop both offensive and defensive perspectives.

---

# Future Topics

Planned additions include:

* Web Application Security
* Active Directory Security
* SIEM Fundamentals
* Threat Hunting
* Malware Analysis
* Cloud Security
* Digital Forensics
* Incident Response
* Security Automation
* Vulnerability Management
* Red Team Methodologies
* Blue Team Operations
* Security Architecture Design

---

# Contributing

Contributions, corrections, and additional learning resources are welcome.

Fork the repository, create a feature branch, and submit a pull request for review.
