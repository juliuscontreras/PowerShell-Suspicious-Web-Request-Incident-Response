# PowerShell Suspicious Web Request Incident Response

This repository contains documentation, Sentinel KQL queries, and analysis details related to a real-world security incident involving suspicious PowerShell-based script downloads and executions.

## 📘 Table of Contents

- [Overview](#overview)
- [MITRE ATT&CK Mapping](#mitre-attck-mapping)
- [Repository Structure](#repository-structure)
- [Security Disclaimer](#security-disclaimer)

## Overview

A suspicious PowerShell activity was detected on an internal host, leading to the download and execution of potentially malicious scripts. This repository captures the detection, investigation, and mitigation efforts.

## MITRE ATT&CK Mapping

- **T1059.001** – PowerShell
- **T1020** – Automated Exfiltration
- **T1086** – Command and Scripting Interpreter
- **T1016** – System Network Configuration Discovery
- **T1203** – Exploitation for Client Execution (Simulated via user action)

## Repository Structure

- `Documentation/`: Guides and reports for incident response and post-analysis.
- `Sentinel_Queries/`: KQL queries used during investigation.
- `Scripts/`: Details about scripts involved in the incident (scripts not included for safety).

## Security Disclaimer

⚠️ **Warning:** This repository references script behaviors that simulate malware or suspicious activity. The actual scripts are **not included** for safety reasons. Never execute PowerShell scripts from untrusted sources on production systems.
