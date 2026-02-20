# Verify BIOS/UEFI Boot Password Protection

|ID          |
|------------|
|CHSTG-FIRM-03|

## Summary

This control aims to determine whether a BIOS/UEFI boot password is required during system startup before the operating system begins loading.

## Test Objectives
- Identify presence of a BIOS/UEFI boot password
- Verify requirement of authentication at system startup
- Confirm protection against unauthorized system boot

## How to Test
1. Ensure the system is powered off.

2. Power on the device.

3. Observe the boot process:
   - Check whether a password prompt appears before the operating system loads
   - Verify whether the system blocks further boot progression until the password is entered

4. Document whether a BIOS/UEFI boot password is required.

## Remediation
Configure a BIOS/UEFI boot password to prevent unauthorized system startup.