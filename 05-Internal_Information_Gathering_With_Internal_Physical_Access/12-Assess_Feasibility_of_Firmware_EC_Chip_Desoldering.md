# Assess Feasibility of Firmware / EC Chip Desoldering

|ID          |
|------------|
|CHSTG-INT-12|

## Summary
This control aims to assess the feasibility and simplicity of desoldering the BIOS/UEFI firmware chip and the Embedded Controller (EC) chip, if present. The objective is to evaluate the level of physical resistance against component removal.

## Test Objectives
- Determine whether firmware and EC chips are technically removable
- Assess ease of physical desoldering
- Evaluate exposure of sensitive components to hardware manipulation

## How to Test
1. Open the device according to standard disassembly procedures.

2. Locate the BIOS/UEFI firmware chip and the Embedded Controller (EC) chip.

3. Evaluate the physical characteristics of each chip:
   - Package type (e.g., SOIC-8, TSOP-8, QFN)
   - Pin accessibility
   - Presence of epoxy, shielding, or protective coating
   - Proximity to other sensitive components

4. Assess whether the chips:
   - Are directly accessible
   - Require removal of shielding
   - Appear easy or complex to desolder based on package type and board layout

5. Document the overall feasibility level (Low / Medium / High).

## Remediation
Apply epoxy resin over sensitive components (e.g., BIOS/UEFI and EC chips) to prevent physical removal or manipulation.