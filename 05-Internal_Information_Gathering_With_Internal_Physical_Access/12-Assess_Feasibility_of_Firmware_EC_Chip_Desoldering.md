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

Examples:

- **Chip 1 WSON**  
![Chip 1 WSON](imgs/BIOS_desoldering1.png)  
The chip is accessible, but plastic connectors (shown in red) are relatively close by. These elements are sensitive to heat and risk melting during desoldering. In orange, you can see very small components (resistors, capacitors) which, although not directly affected by heat, may be displaced or blown away during the operation. In this example, all elements are sufficiently far apart to allow effective protection using KAPTON tape.

- **Chip 2 WSON**  
![Chip 2 WSON](imgs/BIOS_desoldering2.png)  
There are no heat-sensitive components directly near the chip, but small components are very close to the area to be desoldered, which requires extra protection during the operation.  
![Chip 2 WSON with Kapton](imgs/Protected_Bios_desolering_2.png)

- **Chip 3 SOIC-8**  
![Chip 3 SOIC-8](imgs/BIOS_desoldering3.png)  
Although the chip has an SOIC-8 package, which usually makes desoldering easier, the immediate presence of heat-sensitive elements prevents direct removal of the chip. This operation is still possible provided that all nearby elements are removed, and reinforced protection is applied over the sensitive components.

4. Assess whether the chips:
   - Are directly accessible
   - Require removal of shielding
   - Appear easy or complex to desolder based on package type and board layout

5. Document the overall feasibility level (Low / Medium / High).

## Remediation
Apply epoxy resin over sensitive components (e.g., BIOS/UEFI and EC chips) to prevent physical removal or manipulation.