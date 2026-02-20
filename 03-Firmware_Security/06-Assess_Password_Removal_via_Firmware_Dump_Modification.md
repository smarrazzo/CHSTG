# Assess Password Removal via Firmware Dump Modification

|ID          |
|------------|
|CHSTG-FIRM-06|

## Summary

This control aims to assess whether the BIOS/UEFI password protection can be removed through firmware dump extraction and modification when physical access to the system is available.

## Test Objectives
- Determine whether the BIOS/UEFI firmware can be externally accessed
- Identify if firmware dumping tools are compatible with the device
- Assess whether password removal via firmware modification is publicly documented
- Evaluate the overall risk of firmware-level password bypass

## How to Test
1. Identify the BIOS/UEFI storage chip reference (from previous identification steps).

2. Evaluate whether firmware extraction is technically feasible using commonly available SPI programmers, such as:
   - CH341 programmer (typically used with NeoProgrammer)
   - Xgecu T56 programmer (used with Xgpro software)

3. Identify whether access could theoretically be achieved:
   - Via SOIC8 clip (without desoldering)
   - Via desoldering of the BIOS chip

4. Research whether public documentation exists describing password removal through firmware dump modification for the specific device model.

Example:
For HP ProBook systems, documented methods exist:
https://gist.github.com/schorschii/752b3a06f7bc3b33ce7b65ff22c27337

5. Document:
   - Required equipment level (entry-level vs professional tools)
   - Availability of public techniques
   - Technical complexity
   - Risk exposure of the device

## Remediation
Apply epoxy resin over the BIOS/UEFI chip to prevent physical access and unauthorized firmware dumping or rewriting.