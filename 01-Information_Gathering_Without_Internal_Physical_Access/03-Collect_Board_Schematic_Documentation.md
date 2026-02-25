# Collect Board Schematic Documentation

|ID          |
|------------|
|CHSTG-INFO-03|

## Summary

This control aims to locate schematic documentation of the motherboard using the exact board reference identified previously. The objective is to identify the existence and availability of logical circuit diagrams for later hardware analysis without performing any physical interaction with the device.

## Test Objectives
- Identify motherboard schematic documentation
- Determine availability of circuit diagrams
- Identify sources providing access to schematic files

## How to Test
1. Use the motherboard reference identified during test CHSTG-INFO-01.

2. Perform online searches combining the board reference with keywords such as:
   - schematic
   - motherboard schematic
   - board schematic
   - circuit diagram

Example searches (reference from CHSTG-INFO-01 test):

- `DAXK9FMB6C0 schematic`
![DAXK9FMB6C0 schematic](img/00058145.jpg)

- `DA0X8IMB8E0 schematic`
![DA0X8IMB8E0 schematic](img/03-Quanta-X8I-Schematic-da0x8imb8e0.jpg)

- `NB6099C_PCB_MB_MP1.0 schematic`  
  No result found (illustrating the absence of public schematic documentation for certain models).

3. Review search results to determine whether schematic documentation exists.

4. Identify the type of access required:
   - Publicly accessible files
   - Paid download
   - Restricted or VIP access platforms

5. Document the availability and access conditions for later use.

## Remediation
Not applicable.
