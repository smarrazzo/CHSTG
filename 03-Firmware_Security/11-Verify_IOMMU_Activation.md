# Verify IOMMU Activation

|ID          |
|------------|
|CHSTG-FIRM-11|

## Summary

This control aims to verify whether IOMMU-based protection mechanisms are enabled in the BIOS/UEFI configuration after obtaining firmware access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether hardware-based DMA isolation is properly configured.

## Test Objectives
- Identify presence of IOMMU-related features
- Verify whether IOMMU is enabled
- Confirm activation of platform-specific implementations (VT-d / AMD-Vi)

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to advanced, chipset, processor, or security-related sections.

3. Identify configuration options related to IOMMU, such as:
   - IOMMU
   - Intel VT-d
   - AMD-Vi

4. Verify whether these protections are:
   - Present
   - Enabled
   - Configurable

5. Document the activation status and configuration.

## Remediation
Enable IOMMU (Intel VT-d or AMD-Vi) in BIOS/UEFI settings to enforce hardware-level DMA isolation.