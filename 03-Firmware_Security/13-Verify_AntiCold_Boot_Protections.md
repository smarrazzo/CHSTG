# Verify Anti–Cold Boot Protections

|ID          |
|------------|
|CHSTG-FIRM-13|

## Summary

This control aims to verify whether anti–cold boot protections are enabled in the BIOS/UEFI configuration after obtaining firmware access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether memory protection mechanisms are configured to mitigate cold boot attacks.

## Test Objectives
- Identify presence of anti–cold boot protection mechanisms
- Verify whether memory protection features are enabled
- Confirm configuration of RAM protection mechanisms at firmware level

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to advanced, chipset, or security-related sections.

3. Identify configuration options related to memory protection mechanisms, such as:
   - Memory encryption
   - RAM encryption
   - Memory scrambling
   - SRAM scramble
   - Cold boot protection

4. Verify whether these protections are:
   - Present
   - Enabled
   - Configurable

5. Document the protection status and configuration.

## Remediation
Enable all available memory protection mechanisms (e.g., memory encryption, memory scrambling) in BIOS/UEFI settings to mitigate cold boot attack risks.