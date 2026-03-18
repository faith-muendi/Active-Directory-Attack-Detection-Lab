# Active-Directory-Attack-Detection-Lab# Active Directory Attack Detection Lab

## Project Overview

This project simulates an attacker performing reconnaissance and authentication attacks within an internal Active Directory environment. The objective is to demonstrate how a Security Operations Center (SOC) analyst can detect malicious activity using Windows Security Logs and Sysmon telemetry.

The lab replicates a small enterprise network where an attacker gains internal access and begins enumerating systems and services. The attack activities are captured and analyzed to identify indicators of compromise and suspicious behavior.

This project focuses on real-world SOC investigation techniques including network reconnaissance detection, service enumeration monitoring, and authentication failure analysis.

---

## Lab Environment

The following systems were used to simulate the enterprise environment:

| Machine                    | Role                 | IP Address      |
| -------------------------- | -------------------- | --------------- |
| Kali Linux                 | Attacker Machine     | 192.168.206.131 |
| Windows Server 2022 (DC01) | Domain Controller    | 192.168.206.145 |
| Windows Server 2019        | Domain Member Server | 192.168.206.149 |
| Windows Server 2025        | Additional Server    | 192.168.206.153 |

Domain Name:

corp.local

Monitoring Tools:

* Sysmon
* Windows Event Viewer
* Windows Security Logs

---

## Tools Used

* Kali Linux
* Nmap
* Windows Server 2022
* Sysmon
* Windows Event Viewer
* Active Directory Domain Services

---

## Attack Scenario

An attacker gained access to the internal network and began performing reconnaissance against the Active Directory infrastructure. The attacker attempted to discover active hosts, enumerate services, and identify potential authentication weaknesses.

The SOC team investigated the generated logs and detected the malicious activity through Windows Security Events and Sysmon telemetry.

---

## Attack Simulation Steps

### 1. Network Discovery

The attacker used Nmap to discover active systems within the internal network.

Command used:

nmap -sn 192.168.206.0/24

Evidence:

screenshots/network_discovery.png

---

### 2. Domain Controller Port Scanning

The attacker scanned the domain controller to identify exposed services.

Command used:

nmap -sS -sV 192.168.206.145

Evidence:

screenshots/dc_port_scan.png

---

### 3. SMB Protocol Enumeration

The attacker enumerated SMB protocols running on the domain controller.

Command used:

nmap -p445 --script smb-protocols,smb-security-mode 192.168.206.145

Evidence:

screenshots/smb_protocol_scan.png

---

### 4. Authentication Attack Simulation

Multiple failed login attempts were generated against the domain to simulate a credential attack scenario.

These failed authentication attempts produced Windows Security Event ID 4625 which indicates a failed logon attempt.

Evidence:

screenshots/failed_login_events.png

---

## SOC Investigation

The SOC analyst investigated the security logs and identified suspicious activity originating from the Kali Linux attacker machine.

Key events analyzed:

* Event ID 4625 – Failed logon attempt
* Event ID 4624 – Successful logon
* Sysmon Event ID 3 – Network connection activity

These events provided insight into the reconnaissance activity and authentication attack attempts.

---

## Findings

The attacker performed reconnaissance against the internal Active Directory infrastructure and attempted to identify valid credentials through failed authentication attempts.

The attack activity was detectable through Windows Security Logs and Sysmon telemetry. Event ID 4625 revealed multiple failed login attempts indicating a possible brute-force or password spraying attack.

---

## Key Takeaways

This project demonstrates how SOC analysts can detect early stages of an attack within an enterprise environment using log analysis and system monitoring tools.

The lab highlights the importance of monitoring authentication logs and network activity to identify reconnaissance and credential attacks targeting Active Directory environments.

