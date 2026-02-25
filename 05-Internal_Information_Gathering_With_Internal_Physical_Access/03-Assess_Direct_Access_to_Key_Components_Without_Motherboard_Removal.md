# Assess Direct Access to Key Components Without Motherboard Removal

|ID          |
|------------|
|CHSTG-INT-03|

## Summary

This control aims to determine whether key components that could enable hardware-based attacks are directly accessible after removing only the device cover, without requiring full motherboard removal. The objective is to assess the level of protection provided by the device internal layout.

## Test Objectives
- Identify accessibility of security-relevant components
- Determine whether motherboard removal is required for access
- Assess exposure of critical components after minimal disassembly

## How to Test
1. Remove only the external cover of the device (without removing the motherboard).

2. Visually inspect the internal layout.

3. Identify whether the following components are directly accessible:
   - TPM chip
   - BIOS/UEFI chip
   - Embedded Controller (EC)
   - PCIe slots or accessible PCIe-connected devices

4. Determine whether access to these components requires:
   - No additional disassembly
   - Partial removal of shielding
   - Full motherboard removal

5. Document the level of accessibility for each component.

## Remediation
Not applicable.