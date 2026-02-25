# Assess Fast Boot Configuration

|ID          |
|------------|
|CHSTG-BOOT-04|

## Summary

This control aims to determine whether the system uses a fast boot mechanism that reduces or skips parts of the standard initialization process during startup.

## Test Objectives
- Identify if fast boot is enabled
- Determine whether startup checks are shortened
- Assess impact on boot-time security controls

## How to Test
1. Power off the system completely.

2. Power on the device and observe the boot behavior:
   - Very short firmware screen display
   - Boot logo not visible
   - Immediate transition to operating system loading

3. Attempt to access firmware setup during boot:
   - If access is difficult or skipped, fast boot may be enabled

4. If accessible, verify the firmware boot configuration and check the fast boot setting.

5. Document whether fast boot is enabled.

## Remediation
Disable fast boot in firmware settings to ensure full initialization and allow security controls to operate during startup.
