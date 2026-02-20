# Verify ATA Access Password Protection

|ID          |
|------------|
|CHSTG-BOOT-06|

## Summary

This control aims to determine whether an ATA password is configured to protect access to the storage device during system startup.

## Test Objectives
- Identify presence of an ATA disk password
- Confirm disk access restriction before operating system load

## How to Test
1. Ensure the system is powered off.

2. Power on the device.

3. Observe the boot process:
   - Check for a disk password prompt before the operating system loads
   - Verify whether access to the disk is blocked until the password is entered

4. Document whether an ATA password is required.

## Remediation
Enable an ATA disk password in firmware settings to restrict unauthorized access to the storage device.
