# Assess Read/Write Access to Firmware / EC Chip Without Desoldering

|ID          |
|------------|
|CHSTG-INT-13|

## Summary
This control aims to assess whether the BIOS/UEFI firmware chip and the Embedded Controller (EC) chip, if present, could be read from or written to without desoldering. The objective is to evaluate exposure to in-circuit access via physical probing or clip-based techniques.

## Test Objectives
- Determine whether firmware and EC chips are accessible in-circuit
- Assess feasibility of read/write operations without chip removal
- Evaluate exposure of SPI-connected components to direct bus access

## How to Test
1. Open the device according to standard disassembly procedures.

2. Locate the BIOS/UEFI firmware chip and the EC chip.

3. Evaluate physical accessibility:
   - Pin exposure and spacing
   - Package type (e.g., SOIC-8)
   - Presence of conformal coating, epoxy, or shielding
   - Accessibility of SPI traces or test pads

4. Assess whether the board layout appears to allow:
   - In-circuit clip attachment
   - Direct probing of the SPI bus

5. Document the overall feasibility level (Low / Medium / High) based on accessibility and protective measures.

## Remediation
Apply epoxy resin over sensitive components (e.g., BIOS/UEFI and EC chips) to prevent physical read/write access.