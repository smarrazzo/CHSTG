# Assess Possibility to Disable Firmware Protections

|ID          |
|------------|
|CHSTG-FIRM-17|

## Summary

This control aims to assess whether firmware security protections can be disabled without knowing the BIOS/UEFI administrator password by directly modifying firmware NVRAM variables within a firmware dump. The objective is to evaluate the exposure of firmware-level protections to direct manipulation when physical access to the system is available.

## Test Objectives
- Determine whether firmware protections rely on modifiable NVRAM variables
- Assess whether direct firmware variable modification could disable security protections
- Identify exposure of protections such as VT-d, IOMMU, anti-DMA, or memory protections to firmware-level tampering
- Evaluate overall risk of bypassing firmware configuration without BIOS authentication

## How to Test
1. Identify security protections enabled in BIOS/UEFI (e.g., VT-d, IOMMU, anti-DMA, memory protections).

2. Assess whether the firmware configuration is stored in NVRAM variables that could theoretically be altered through firmware dump manipulation.

3. Based on empirical testing and internal research experience, certain systems (e.g., HP 430 G6) may store protection states in variables such as:
   - `IntelTechnologieOptions`
   - `S3MemoryVariable`

4. Evaluate whether security protections appear to be variable-based and therefore potentially modifiable outside normal BIOS authentication mechanisms.

5. Document:
   - Whether protections appear NVRAM-based
   - Technical feasibility of modification
   - Required level of expertise
   - Overall exposure of firmware protections to direct manipulation

## Remediation
Apply epoxy resin over the BIOS/UEFI chip to prevent physical access and unauthorized firmware reading or writing.