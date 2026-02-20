# Assess Full Automatic Boot Behavior

|ID          |
|------------|
|CHSTG-BOOT-03|

## Summary

This control aims to determine whether the system automatically boots to the login screen without requiring any user interaction, such as a disk decryption PIN or pre-boot authentication.

## Test Objectives
- Identify if the system performs a fully automatic boot
- Detect absence of pre-boot authentication mechanisms
- Determine whether user interaction is required before the login screen

## How to Test
1. Ensure the system is powered off.

2. Power on the device.

3. Observe the boot process:
   - Check if a pre-boot authentication screen appears (PIN, password, smart card, etc.)
   - Check if disk decryption credentials are required

4. Determine system behavior:
   - If the system reaches the operating system login screen without any user interaction → automatic boot
   - If credentials are required before the login screen → protected boot

5. Document the observed behavior.

## Remediation
Enable pre-boot authentication (for example full disk encryption with pre-boot PIN or password) to prevent unauthorized system access during startup.
