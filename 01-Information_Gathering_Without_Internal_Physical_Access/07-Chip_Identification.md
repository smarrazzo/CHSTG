# Chip Identification

|ID          |
|------------|
|CHSTG-INFO-07|

## Summary

This control aims to identify key internal components such as the BIOS/UEFI chip, the embedded controller, and the TPM chip using publicly available documentation. The identification is performed using high-resolution motherboard images, boardview files, or schematic files without physically accessing the device.

## Test Objectives
- Identify BIOS/UEFI storage chip
- Identify embedded controller chip
- Identify TPM chip
- Determine chip references and manufacturers

## How to Test
1. Use the motherboard reference identified during test CHSTG-INFO-01.

2. Collect visual documentation of the motherboard:
   - High-resolution photos from spare parts resellers
   - Repair or refurbishment marketplaces
   - Technical forums

3. If available, use boardview files to locate and identify components.

4. If available, use schematic files to confirm chip roles and references.

5. Correlate information between photos, boardview, and schematic to confirm component identification.

6. Document the identified chips and their references for later hardware analysis.

## Remediation
Not applicable.
