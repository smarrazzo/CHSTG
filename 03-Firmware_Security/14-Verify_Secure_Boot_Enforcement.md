# Verify Secure Boot Enforcement

|ID          |
|------------|
|CHSTG-FIRM-14|

## Summary

This control aims to verify whether Secure Boot is properly enabled and enforced in the BIOS/UEFI configuration after obtaining firmware access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to ensure that Secure Boot is activated and not configured in enrollment or permissive mode.

## Test Objectives
- Identify presence of Secure Boot feature
- Verify whether Secure Boot is enabled
- Confirm that Secure Boot is not configured in enrollment mode
- Assess overall enforcement of boot integrity controls

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to the Secure Boot or security-related section.

3. Identify the Secure Boot configuration status:
   - Secure Boot enabled or disabled
   - Mode (Standard / Custom / Enrollment)

4. Verify that:
   - Secure Boot is enabled
   - The system is not in enrollment mode
   - Secure Boot keys are properly installed

5. Document the Secure Boot status and configuration mode.

## Remediation
Enable Secure Boot in standard enforcement mode and ensure the system is not configured in enrollment or permissive mode.