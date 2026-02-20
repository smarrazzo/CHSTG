# Verify Virtualization Activation

|ID          |
|------------|
|CHSTG-FIRM-16|

## Summary

This control aims to verify whether hardware virtualization features are enabled in the BIOS/UEFI configuration after obtaining firmware access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether processor-level virtualization support is activated.

## Test Objectives
- Identify presence of hardware virtualization features
- Verify whether virtualization is enabled
- Confirm activation of platform-specific implementations (VT-x / AMD-V)

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to advanced, processor, or chipset-related sections.

3. Identify configuration options related to virtualization, such as:
   - Virtualization Technology
   - Intel VT-x
   - AMD-V

4. Verify whether these features are:
   - Present
   - Enabled
   - Configurable

5. Document the activation status and configuration.

## Remediation
Enable hardware virtualization features (Intel VT-x or AMD-V) in BIOS/UEFI settings when required for secure virtualization-based workloads.