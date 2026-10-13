Project 3: Windows 11 Endpoint Troubleshooting and Incident Resolution

Overview

This project documents practical Windows 11 endpoint troubleshooting and health verification in a Microsoft 365 lab environment. The objective was to investigate common endpoint concerns, collect evidence, verify system and application status, and document findings without making unnecessary configuration changes.

Lab Environment

Device: INTUNE-USER

Operating system: Windows 11 Enterprise Evaluation, version 25H2

Management: Microsoft Intune and Microsoft Entra ID

Primary user: MD102 Test User

Tools: Windows Settings, Services, Event Viewer, PowerShell, Microsoft Intune admin center

Incident 01: Windows Update Health Investigation

Incident ID: INC-301

Investigation

Checked Windows Update status in Settings.

Inspected the Windows Update service.

Reviewed update history and confirmed successful Security Update and .NET Framework Security Update installations.

Found WindowsUpdateClient Event ID 25 with error 0x80244022.

Performed a new update check.

Outcome

The new update check succeeded and Windows reported that it was up to date. The historical error was consistent with a temporary update-service availability issue, but its exact cause was not confirmed.

Status: Investigation completed; no current update failure reproduced.

Incident 02: Application Deployment Verification

Incident ID: INC-302

Investigation

Searched for 7-Zip in Start.

Launched 7-Zip File Manager successfully.

Reviewed the app's Intune deployment status.

Confirmed the device-level installation status was Installed.

The user install-status summary showed one install, zero failures and zero pending installs.

Outcome

The application was installed and working. No installation failure was reproduced, and no corrective action was required.

Status: Verification completed successfully.

Incident 03: Windows Time Service Investigation

Incident ID: INC-303

Investigation

Checked the Windows Time (W32Time) service in Services.

Confirmed the service was running with startup type Manual.

Ran w32tm /query /status.

Verified a successful synchronisation was recorded with time.windows.com.

Ran Get-Date and confirmed the displayed date and time were correct.

Outcome

No current time-synchronisation fault was identified. The Manual startup type was not treated as a fault on its own, and no configuration changes were made.

Status: Investigation completed; no fault found.

Incident 04: Windows Endpoint Health Check

Incident ID: INC-304

Investigation

Used Get-ComputerInfo to inspect Windows identity and build information.

Used winver to verify Windows version 25H2 and Enterprise Evaluation.

Ran sfc /verifyonly; no integrity violations were found.

Ran chkdsk C: /scan; Windows found no file-system problems and reported that no further action was required.

Used Get-Volume to check the C: drive.

Confirmed the volume was NTFS, Healthy and operational, with approximately 38.4 GB free out of 67.6 GB.

Used Get-MpComputerStatus to check Microsoft Defender.

Outcome

The checks found no system-file integrity violations or file-system problems. Storage health and available capacity were satisfactory. Defender's service, antivirus and real-time protection checks all returned True. Signature freshness was not verified.

Status: Basic health assessment completed; no fault found in the checks performed.

Incident 05: Intune Device Management Verification

Incident ID: INC-305

Investigation

Located INTUNE-USER in the Intune admin center.

Confirmed the device was marked Compliant and Corporate.

Confirmed the primary user was MD102 Test User.

Reviewed the device's last check-in timestamp.

Outcome

The Intune device record showed the device as Compliant, with the expected ownership and primary user. The last check-in displayed was 13 October 2026 at 04:20 AM.

Status: Device record verification completed.

Technical Skills Practised

Windows Update health checks and event-log investigation

Windows application verification and Intune deployment-status review

Windows service inspection and time-synchronisation checks

PowerShell system-information and health-check commands

System-file and file-system verification

Disk-space and volume-health assessment

Microsoft Defender status checks

Intune device compliance and management-record verification

Technical documentation and evidence-based troubleshooting

Project Limitations

These were controlled lab investigations. Most checks did not reveal an active fault, so the project demonstrates investigation and verification rather than five repairs. The historical Windows Update error's root cause was not conclusively established. The Intune check-in timestamp is the value displayed in the admin center and was not independently correlated with a device-side timestamp.

Conclusion

This project demonstrates a structured approach to Windows endpoint support: inspect the reported state, collect technical evidence, validate results, avoid unnecessary changes, and document findings accurately. It provides a foundation for further practice with real-world Windows 11 and Microsoft Intune support scenarios.
