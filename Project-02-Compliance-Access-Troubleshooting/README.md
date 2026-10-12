# Endpoint Compliance and Access Troubleshooting

## Project Overview

This project documents a simulated enterprise access incident investigated using Microsoft Entra ID, Microsoft Intune, and a Windows 11 test VM.

The investigation began with a browser certificate warning while accessing Microsoft 365. The work demonstrates evidence-based troubleshooting, identity sign-in log analysis, Windows service checks, and post-remediation validation.

## Incident Details

- **Incident ID:** INC-1042
- **Affected user:** MD102 Test User
- **Environment:** Windows 11 Enterprise test VM managed by Microsoft Intune
- **Affected service:** Microsoft 365 / SharePoint Online
- **Initial symptom:** Browser displayed `NET::ERR_CERT_DATE_INVALID` with the message “Your connection is not private.”
- **Status:** Access restored; root cause not fully confirmed

## Investigation

### 1. Microsoft Entra sign-in logs

The Entra sign-in logs contained successful events for the test user:

- **Application:** Office 365 SharePoint Online
- **Result:** Success
- **Error code:** `0`

A related SharePoint Web Client Extensibility event also showed a successful sign-in, with multifactor authentication indicated.

These results showed successful authentication for the recorded events. They did not, by themselves, prove that every SharePoint resource was accessible or that Conditional Access caused the original browser warning.

### 2. Browser certificate warning

The Windows 11 VM displayed:

`NET::ERR_CERT_DATE_INVALID`

This indicated a certificate date/validity problem from the browser's perspective. The Windows Time service was then found to be stopped.

### 3. Remediation

The Windows Time service was started using the Windows Services interface.

After this action, the user reported that the environment was working again. The browser warning and access issue were therefore treated as resolved for the test.

The available evidence suggests that Windows time synchronisation may have contributed to the certificate warning, but the precise cause was not conclusively verified with a recorded clock comparison or certificate inspection.

### 4. Validation

After the service was started, the user reported that the environment worked. A screenshot was saved as project evidence.

## Evidence

| Evidence | Description |
|---|---|
| [SharePoint access restored](Evidence/Project-02-01-SharePoint-Access-Restored.png) | Screenshot captured after the reported recovery |

## Outcome

- Reviewed Microsoft Entra sign-in events for the test user.
- Identified successful SharePoint-related authentication events.
- Investigated a browser TLS certificate date warning.
- Found the Windows Time service stopped and started it.
- Confirmed that the environment subsequently worked, based on user validation.

## Lessons Learned

- A browser certificate warning should not automatically be attributed to Conditional Access.
- Successful authentication events do not guarantee access to every application resource.
- System time is an important part of certificate validation.
- Troubleshooting should use observable evidence and avoid claiming an unverified root cause.

## Skills Demonstrated

- Microsoft Entra ID sign-in log analysis
- Windows 11 troubleshooting
- Windows Time service investigation
- TLS certificate error triage
- Evidence-based remediation and validation
- Technical incident documentation
