# Verify PCIe Anti-DMA Protection Status

|ID          |
|------------|
|CHSTG-FIRM-08|

## Summary

This control aims to verify whether PCIe anti-DMA protections are enabled in the BIOS/UEFI configuration after obtaining firmware access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether protections against unauthorized DMA access are properly configured.

## Test Objectives
- Identify presence of anti-DMA protection mechanisms
- Verify status (enabled/disabled) of PCIe DMA protections
- Confirm firmware-level configuration of DMA mitigation features

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to advanced or security-related sections.

3. Identify configuration options related to DMA protection, such as:
   - IOMMU
   - Intel VT-d
   - AMD-Vi
   - Anti-DMA Protection
   - DMA Protection
   - Pre-boot DMA Protection

4. Verify whether these protections are:
   - Present
   - Enabled
   - Configurable

5. Document the protection status and any configurable parameters.

## Remediation
Enable all available PCIe DMA protection mechanisms in BIOS/UEFI settings (e.g., IOMMU, VT-d, AMD-Vi, Pre-boot DMA Protection) to mitigate unauthorized direct memory access attacks.