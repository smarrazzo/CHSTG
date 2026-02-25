# Verify Thunderbolt/USB4 Anti-DMA Protection Status

|ID          |
|------------|
|CHSTG-FIRM-09|

## Summary

This control aims to verify whether Thunderbolt and/or USB4 anti-DMA protections are enabled in the BIOS/UEFI configuration after obtaining firmware access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether protections against unauthorized DMA access through external high-speed interfaces are properly configured.

## Test Objectives
- Identify presence of Thunderbolt anti-DMA protection mechanisms
- Identify presence of USB4 DMA protection mechanisms
- Verify whether these protections are enabled
- Confirm firmware-level configuration of interface-specific DMA mitigations

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to advanced, security, or Thunderbolt/USB configuration sections.

3. Identify configuration options related to DMA protection, such as:
   - USB4 DMA Protection
   - Thunderbolt DMA Protection
   - Thunderbolt Security Level
   - Pre-boot Thunderbolt Protection

4. Verify whether these protections are:
   - Present
   - Enabled
   - Configurable

5. Document the protection status and any configurable parameters.

## Remediation
Enable all available Thunderbolt and USB4 DMA protection mechanisms in BIOS/UEFI settings to mitigate unauthorized direct memory access attacks via external high-speed interfaces.