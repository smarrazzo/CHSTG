# Verify Security PIN Code Requirement at Boot

|ID          |
|------------|
|CHSTG-BOOT-05|

## Summary

This control aims to determine whether a security PIN code is required during system startup before the operating system loads.

## Test Objectives
- Identify presence of a boot security PIN
- Confirm requirement of user interaction before system startup

## How to Test
1. Ensure the system is powered off.

2. Power on the device.

3. Observe the boot process:
   - Check for a pre-boot PIN prompt
   - Verify whether the system blocks startup until the PIN is entered

4. Document whether a startup PIN is required.

## Remediation
Enable a boot security PIN in firmware or disk encryption configuration to prevent unauthorized system startup.
