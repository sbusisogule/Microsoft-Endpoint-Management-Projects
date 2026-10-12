# LAB-25 — Final Integrated Endpoint Management Scenario

## Objective

Demonstrate an end-to-end Microsoft Intune and Microsoft Entra ID endpoint management scenario by validating the configuration, security, compliance, application deployment, and management state of a Windows 11 test device.

## Scenario

A new Windows 11 corporate device has been provided to an employee.

As the endpoint administrator, the objective is to ensure that the device is:

* Microsoft Entra joined
* Enrolled and managed by Microsoft Intune
* Assigned to the correct primary user
* Compliant with organizational requirements
* Protected using Windows security controls
* Configured with Windows Hello
* Managed using Windows LAPS
* Protected by Windows Firewall
* Configured with required endpoint applications
* Managed through the organization's endpoint management policies

## Test Environment

| Item                | Value                 |
| ------------------- | --------------------- |
| Device              | INTUNE-USER           |
| Operating System    | Windows 11 Enterprise |
| Primary User        | MD102 Test User       |
| Management Platform | Microsoft Intune      |
| Identity Platform   | Microsoft Entra ID    |
| Ownership           | Corporate             |
| Compliance          | Compliant             |

## Validation

### Microsoft Entra ID

The device was verified using:

```text
dsregcmd /status
```

Device state:

```text
AzureAdJoined : YES
EnterpriseJoined : NO
DomainJoined : NO
Virtual Desktop : NOT SET
Device Name : Intune-User
```

Result: **PASS**

### Microsoft Intune Management

The device was verified in Intune with the following state:

* Device: INTUNE-USER
* Managed by: Intune
* Ownership: Corporate
* Primary user: MD102 Test User
* Compliance: Compliant

Result: **PASS**

### Secure Boot

Windows System Information reported:

```text
Secure Boot State: On
```

Result: **PASS**

### TPM

The TPM management console reported:

```text
The TPM is ready for use
```

Result: **PASS**

### Windows Hello

Windows Sign-in Options displayed:

* Change PIN
* I forgot my PIN

This confirmed that a Windows Hello PIN was configured.

Result: **PASS**

### Windows LAPS

The LAB-05 Windows LAPS policy was previously configured and assigned to the MD-102 pilot group.

The local PowerShell retrieval test could not be completed because the Microsoft Graph PowerShell dependency was not installed on the test VM.

Result: **CONFIGURATION VALIDATED — PASSWORD RETRIEVAL NOT VALIDATED**

### Win32 Application

The 7-Zip Win32 application created during LAB-23 was verified as installed on the Windows 11 test device.

Result: **PASS**

### Windows Firewall

Windows Defender Firewall with Advanced Security was checked on the test device.

Firewall state was reported as:

```text
On
```

Result: **PASS**

## Policies and Controls Used

The capstone environment incorporated controls created throughout the MD-102 lab program, including:

* LAB-01 — Windows 11 Standard Configuration
* LAB-02 — Windows 11 Basic Compliance
* LAB-05 — Windows LAPS
* LAB-07 — Windows Defender Antivirus
* LAB-08 — Windows Firewall
* LAB-09 — Windows Firewall RDP Rule
* LAB-13 — BitLocker
* LAB-20 — Windows Update Ring
* LAB-21 — Windows 11 25H2 Feature Update
* LAB-22 — Windows Update Compliance
* LAB-23 — Win32 Application Deployment
* LAB-24 — Windows Time Service Remediation

## Troubleshooting

During the capstone validation, several observations demonstrated realistic endpoint administration challenges.

### Windows Update settings

The Windows Settings interface did not expose every Intune Update Ring configuration setting directly.

The update configuration was therefore treated as an Intune-side management control rather than assuming that every policy setting would appear in the local Windows Settings interface.

### Windows LAPS

The `Get-LapsAADPassword` command required Microsoft Graph PowerShell functionality that was not installed on the test VM.

The LAPS policy configuration was therefore documented as configured, while password retrieval was not claimed as successfully validated.

### Intune reporting

Some Intune policies and remediation reports did not immediately contain device results.

The lab therefore avoided treating delayed reporting as a configuration failure and validated the controls that could be directly confirmed on the endpoint and in Intune.

## Lessons Learned

This capstone demonstrated that endpoint administration is not simply about creating Intune policies.

An administrator must be able to:

1. Identify the device and user.
2. Verify Microsoft Entra join status.
3. Confirm Intune management.
4. Validate compliance.
5. Verify endpoint security controls.
6. Confirm application deployment.
7. Distinguish configuration from successful execution.
8. Troubleshoot reporting and dependency issues.
9. Document evidence accurately.
10. Avoid claiming success when a control has not actually been validated.

## Conclusion

The LAB-25 test device successfully demonstrated an integrated Microsoft Entra ID and Microsoft Intune endpoint management scenario.

The device was confirmed as:

* Microsoft Entra joined
* Intune managed
* Corporate owned
* Assigned to the correct primary user
* Compliant
* Protected by Secure Boot
* TPM ready
* Configured for Windows Hello
* Protected by Windows Firewall
* Equipped with the required 7-Zip Win32 application

The Windows LAPS configuration was confirmed, although password retrieval was not validated because the required Microsoft Graph PowerShell dependency was unavailable on the test device.

This concludes the structured MD-102 endpoint management laboratory program.
