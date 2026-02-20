# Assess Password Removal via Unlocked Firmware Image

|ID          |
|------------|
|CHSTG-FIRM-07|

## Summary

This control aims to assess whether the BIOS/UEFI password protection can be bypassed by flashing an unlocked firmware image previously identified during CHSTG-INFO-06. The objective is to evaluate the exposure of the device to firmware replacement attacks when physical access is available.

## Test Objectives
- Determine whether unlocked firmware images exist for the device model
- Assess feasibility of flashing an alternative firmware image
- Identify required equipment for firmware rewriting
- Evaluate the overall risk of password bypass through firmware replacement

## How to Test
1. Confirm that an unlocked or modified firmware image has been identified during CHSTG-INFO-06.

2. Identify the BIOS/UEFI storage chip reference (from previous identification steps).

3. Assess whether firmware rewriting would be technically feasible using commonly available SPI programmers, such as:
   - CH341 programmer (typically used with NeoProgrammer)
   - Xgecu T56 programmer (used with Xgpro software)

4. Identify whether physical access to the firmware chip would theoretically allow:
   - In-circuit access via SOIC8 clip (without desoldering)
   - Direct chip access after desoldering

5. Document:
   - Availability of unlocked firmware images
   - Required equipment level (entry-level vs professional tools)
   - Technical complexity
   - Risks associated with firmware replacement (hardware incompatibility, firmware corruption)
   - Overall exposure of the device to firmware replacement attacks

## Remediation
Apply epoxy resin over the BIOS/UEFI chip to prevent physical access and unauthorized firmware rewriting.