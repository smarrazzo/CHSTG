# Check for Default BIOS/UEFI Passwords

|ID          |
|------------|
|CHSTG-FIRM-04|

## Summary

This control aims to determine whether the BIOS/UEFI password configured on the system corresponds to a default or weak password (e.g., "123456", "admin", etc.).

## Test Objectives
- Identify use of default BIOS/UEFI passwords
- Identify use of weak or easily guessable passwords
- Assess strength of firmware access protection

## How to Test
1. Ensure a BIOS/UEFI password is configured (as identified in previous tests).

2. During system startup, access the BIOS/UEFI interface.

3. Attempt authentication using common default credentials such as:
   - 123456
   - admin
   - password
   - manufacturer name

4. Observe system behavior:
   - If access is granted using a common/default password → insecure configuration
   - If access is denied → password is not default (or not weak)

5. Document whether a default or weak password is in use.

## Remediation
Configure a strong, unique BIOS/UEFI password that is not based on default or easily guessable values.