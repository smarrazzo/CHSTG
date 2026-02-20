# Verify Pre-Boot DMA Protection

|ID          |
|------------|
|CHSTG-FIRM-10|

## Summary

This control aims to verify whether pre-boot DMA protection mechanisms are enabled in the BIOS/UEFI configuration after obtaining firmware access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether DMA protections are enforced before the operating system loads.

## Test Objectives
- Identify presence of pre-boot DMA protection mechanisms
- Verify whether pre-boot DMA protection is enabled
- Confirm enforcement of DMA restrictions before operating system startup

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to advanced or security-related sections.

3. Identify configuration options related to pre-boot DMA protection, such as:
   - Pre-Boot DMA Protection
   - DMA Protection (Pre-OS)
   - Pre-boot Thunderbolt Protection (if applicable)

4. Verify whether these protections are:
   - Present
   - Enabled
   - Configurable

5. Document the protection status and configuration.

## Remediation
Enable pre-boot DMA protection in BIOS/UEFI settings to ensure DMA mitigation mechanisms are enforced before the operating system loads.