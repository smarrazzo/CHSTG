# Identify TPM Presence

|ID          |
|------------|
|CHSTG-INT-14|

## Summary

This control aims to identify the presence of a Trusted Platform Module (TPM) on the motherboard, determine its exact physical location, and record its precise component reference. The objective is to document the TPM implementation for further hardware analysis.

## Test Objectives
- Identify presence of a TPM chip
- Determine exact physical location on the motherboard
- Record manufacturer and model reference

## How to Test
1. Open the device according to standard disassembly procedures.

2. Visually inspect the motherboard for a dedicated TPM chip.

3. Identify:
   - Chip marking (manufacturer and model)
   - Package type
   - Exact board location

4. If necessary, correlate with board silkscreen labels or schematic/boardview information to confirm identification.

5. Document:
   - TPM presence (Yes / No)
   - Exact chip reference
   - Physical location on the motherboard

## Remediation
Apply epoxy resin over sensitive components such as the TPM chip to prevent physical tampering.