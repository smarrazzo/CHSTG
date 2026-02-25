# Verify TPM Clearing Protection via Anti-Tamper

|ID          |
|------------|
|CHSTG-FIRM-20|

## Summary

This control aims to verify whether the firmware is configured to clear the TPM automatically upon detection of chassis opening after obtaining BIOS/UEFI access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether a tamper event triggers TPM data invalidation as a protective measure.

## Test Objectives
- Identify presence of TPM clearing mechanism linked to chassis intrusion detection
- Verify whether automatic TPM clearing is enabled
- Confirm firmware-level configuration of tamper-triggered TPM protection

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to security, TPM, or anti-tamper related sections.

3. Identify configuration options such as:
   - Clear TPM on boot after cover opening
   
4. Verify whether these mechanisms are:
   - Present
   - Enabled
   - Configurable

5. Document the configuration status and protection behavior.

## Remediation
Enable TPM clearing upon chassis intrusion detection in BIOS/UEFI settings to protect cryptographic material against physical tampering.