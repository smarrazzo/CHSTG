# Collect Chip Datasheets

|ID          |
|------------|
|CHSTG-INFO-08|

## Summary

This control aims to collect technical documentation (datasheets) of the components previously identified. The objective is to obtain the official electrical and functional specifications of each chip using publicly available documentation without interacting physically with the device.

## Test Objectives
- Locate datasheets of identified components
- Determine chip electrical characteristics
- Identify pinout and functional description

## How to Test
1. Use the chip references identified during test CHSTG-INFO-07.

2. Perform online searches combining the chip reference with the keyword:
   - datasheet

Example:
`W25Q128 datasheet`

Example of datasheet:
https://www.winbond.com/resource-files/w25q128jv%20revf%2003272018%20plus.pdf

3. Prefer manufacturer official sources when available.

4. Archive the datasheets for later hardware analysis.

## Remediation
Not applicable.
