# Verify Anti-Tamper Enforcement on Power-Off

|ID          |
|------------|
|CHSTG-FIRM-19|

## Summary

This control aims to verify whether the firmware is configured to automatically power off the system upon detection of chassis opening after obtaining BIOS/UEFI access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether active enforcement mechanisms are configured in response to physical intrusion detection.

## Test Objectives
- Identify presence of automatic shutdown mechanisms triggered by chassis intrusion
- Verify whether power-off enforcement is enabled
- Confirm configuration of firmware response to tamper detection

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to security or anti-tamper related sections.

3. Identify configuration options such as:
   - Power off upon cover opening

4. Verify whether these mechanisms are:
   - Present
   - Enabled
   - Configurable

5. Document the enforcement status and configuration.

## Remediation
Enable automatic power-off or shutdown enforcement upon chassis intrusion detection in BIOS/UEFI settings.