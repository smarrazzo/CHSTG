# Assess Network Boot Accessibility

|ID          |
|------------|
|CHSTG-BOOT-08|

## Summary

This control aims to determine whether the system allows booting from the network during startup.

## Test Objectives
- Identify availability of network boot option
- Determine if the user can initiate a network boot
- Assess boot restriction enforcement

## How to Test
1. Power on the device.

2. Access the boot selection menu (boot menu key during startup).

3. Observe available boot options:
   - Network boot (PXE)

4. Attempt to select the network boot option.

5. Document whether network boot is allowed or restricted.

## Remediation
Disable network boot in firmware settings and protect boot configuration with an administrator password.
