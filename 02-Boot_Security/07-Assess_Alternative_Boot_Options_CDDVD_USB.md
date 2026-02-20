# Assess Alternative Boot Options (CD/DVD, USB)

|ID          |
|------------|
|CHSTG-BOOT-07|

## Summary

This control aims to determine whether the system allows booting from alternative devices such as CD/DVD or USB during startup.

## Test Objectives
- Identify availability of alternative boot devices
- Determine if the user can select another boot source
- Assess boot restriction enforcement

## How to Test
1. Power on the device.

2. Access the boot selection menu (boot menu key during startup).

3. Observe available boot options:
   - Internal storage
   - USB devices
   - CD/DVD devices

4. Attempt to select an alternative boot device.

5. Document whether alternative boot is allowed or restricted.

## Remediation
Restrict alternative boot devices in firmware settings and protect boot configuration with an administrator password.
