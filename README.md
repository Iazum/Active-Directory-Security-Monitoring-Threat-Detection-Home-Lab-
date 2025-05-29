# Active-Directory-Security-Monitoring-Threat-Detection-Home-Lab-

## Overview
This project demonstrates a simulated enterprise security monitoring environment. It focuses on building and securing an Active Directory (AD) domain, collecting logs with Splunk, simulating cyberattacks, and analyzing events for threat detection

The home lab was built using virtual machines on a host system, simulating a complete IT infrastructure, including a Domain Controller, endpoint devices, a centralized log management system, and an attacker machine

## Lab Environment
- Windows Server 2019 - Active Directory Domain Controller
- Windows 11 - Domain joined Workstation for attacking simulation and endpoint monitoring
- Ubuntu Server - Splunk Enterprise instance for log aggregation and SIEM functionality
- Kali Linux - Attack simulation using tools like 'crowbar'

## Project Objectives
- Deploy and configure a functional Active Directory domain
- Forward Windows Event Logs to Splunk for centralized monitoring
- Simulate brute-force attacks and adversary behaviour
- Generate endpoint telemetry using Atomic Red Team
- Correlate events, detect threats, and generate incident response insights

## Configuration & Implementation

## Active Directory Deployment
- Created an internal domain 'mydfir.local' using Windows Server 2019
- Managed Group Policy Objects (GPOs) for basic security hardening
- Creaeted multiple domain user accounts to simulate an enterprise environment

## Log Collection with Splunk
- Installed **Splunk Enterprise** on Ubuntu Server
- Configured **Universal Forwarder** on Windows 11 to forward logs (e.g Security, System, Application)
- Built dashboards in Splunk to monitor logon failures, privilege escalations and process execution

## Simulated Attacks
- **Brute-force attack** using 'crowbar' from kali linux targeting RDP and SMB authentication
- **Atomic Red Team** techniques executed on Windows 11:
    - Credential dumping
    - Powershell execution
    - Service persistence
    - Unusual child processes
 
> Goal: Validate detection of MITRE ATT&CK techniques in a simulated Blue Team workflow


## Detection Use Cases
Use Case
> Brute Force (Event ID 4625) - 'index=wineventlog EventCode=4625'
> Successful Login (4624) - 'index=wineventlog EventCode=4625 Logon_Type=10'
> Powershell Execution - 'index=wineventlog ParentImage=*powershell.exe*'

## Sample Logs
- Brute-Force Login attempts
- Windows Event Log sample highlighting suspicious activity
- Terminal output from Atomic Red Team executions
## Key Components 
- Designed and deployed and AD domain with custom users and GPOs
- Installed and configured ** Splunk ** on Ubuntu to ingest logs from Windows machines
- Simulated **brute-force attacks** 
