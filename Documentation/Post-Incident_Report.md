# 🛡️ Post-Incident Report

## 📌 Incident Summary

- **Name:** JuliusC - PowerShell Suspicious Web Request
- **Affected Host:** windows-target-1
- **Date:** April 17, 2025
- **Detection Source:** Microsoft Defender for Endpoint

## 🔍 Detection and Analysis

### Scripts Involved

- portscan.ps1
- pwncrypt.ps1
- exfiltratedata.ps1
- eicar.ps1

### Execution Method

Scripts downloaded via `Invoke-WebRequest` and executed from `C:\programdata`.

### User Interview

User admitted to downloading a "free piece of software." Experienced a brief screen flash, but no apparent activity.

### Execution Confirmation

Confirmed using Sentinel KQL:

```kql
let TargetHostname = "windows-target-1";
let ScriptNames = dynamic(["eicar.ps1", "exfiltratedata.ps1", "portscan.ps1", "pwncrypt.ps1"]);
DeviceProcessEvents
| where DeviceName == TargetHostname
| where FileName == "powershell.exe"
| where ProcessCommandLine contains "-File" and ProcessCommandLine has_any (ScriptNames)
| project TimeGenerated, AccountName, DeviceName, FileName, ProcessCommandLine
```

## 🧪 Malware Analysis Summary

- **portscan.ps1:** Internal reconnaissance via port scan.
- **pwncrypt.ps1:** Simulates ransomware with fake encryption/ransom note.
- **exfiltratedata.ps1:** Simulated data exfiltration via Azure Blob upload.
- **eicar.ps1:** EICAR test string for AV detection.

## 🔒 Containment and Recovery

- Host isolated, scanned, cleaned, and reintegrated.
- No persistent threats found.

## 📘 Post-Incident Measures

- Cybersecurity training refreshed.
- Enhanced PowerShell policy enforcement.
