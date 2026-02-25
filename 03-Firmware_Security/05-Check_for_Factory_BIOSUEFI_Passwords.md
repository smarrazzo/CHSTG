# Check for Factory BIOS/UEFI Passwords

|ID          |
|------------|
|CHSTG-FIRM-05|

## Summary

This control aims to determine whether a manufacturer factory password exists that could bypass the configured BIOS/UEFI protection.

## Test Objectives
- Identify existence of manufacturer backdoor passwords
- Assess risk of firmware protection bypass
- Verify robustness of BIOS/UEFI password implementation

## How to Test
1. Ensure a BIOS/UEFI password is configured and active.

2. Attempt to access the BIOS/UEFI interface and trigger a password failure (if required to obtain an unlock code or system hash).

3. Record any displayed halt code, challenge code, or system identifier shown after failed authentication attempts.

4. Use publicly available resources to determine whether a factory or master password exists for the device model.

Example resource:
https://bios-pw.org/

5. Attempt authentication using any derived factory or master password (without modifying system settings).

6. Document whether the firmware protection can be bypassed using a manufacturer password.

## Remediation
Update the system firmware to the latest version and ensure that factory or master password mechanisms are disabled or mitigated when supported by the manufacturer.