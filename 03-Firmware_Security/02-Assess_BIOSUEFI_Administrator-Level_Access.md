# Assess BIOS/UEFI Administrator-Level Access

|ID          |
|------------|
|CHSTG-FIRM-02|

## Summary

This control aims to determine whether BIOS/UEFI configuration settings can be modified without authentication. The objective is to verify the presence of an administrator password protecting firmware configuration changes.

## Test Objectives
- Identify whether BIOS/UEFI settings can be modified without authentication
- Verify presence of an administrator password
- Determine whether configuration changes are properly restricted

## How to Test
1. Power on the system.

2. Access the BIOS/UEFI setup interface during startup.

3. Attempt to modify a non-critical configuration setting (without saving changes).

4. Observe system behavior:
   - If modifications are allowed without authentication → no administrator protection
   - If a password prompt appears before modification → administrator protection enabled

5. Verify whether a password is required:
   - To access configuration menus
   - Or specifically when attempting to modify settings

6. Document whether firmware modification is protected by a password.

## Remediation
Configure a BIOS/UEFI administrator password to prevent unauthorized modification of firmware settings.