# Assess BIOS/UEFI User-Level Access

|ID          |
|------------|
|CHSTG-FIRM-01|

## Summary

This control aims to determine whether BIOS/UEFI configuration information can be accessed without authentication. The objective is to verify if a read-only access is possible and whether security-related settings can be viewed without requiring credentials.

## Test Objectives
- Identify whether BIOS/UEFI setup is accessible without authentication
- Determine if configuration settings are readable without credentials
- Verify visibility of security-related settings (anti-tamper, anti-DMA, etc.)

## How to Test
1. Power on the system.

2. Access the BIOS/UEFI setup interface during startup.

3. Observe whether authentication is required before accessing the configuration menus.

4. If access is granted without authentication:
   - Navigate through security-related sections
   - Identify visibility of settings such as:
     - Anti-tamper mechanisms
     - Anti-DMA protections
     - Secure Boot configuration
     - Boot order configuration

5. Document whether:
   - Access is unrestricted
   - Access is read-only
   - Authentication is required

## Remediation
Configure a BIOS/UEFI administrator password to restrict unauthorized access to firmware configuration settings.