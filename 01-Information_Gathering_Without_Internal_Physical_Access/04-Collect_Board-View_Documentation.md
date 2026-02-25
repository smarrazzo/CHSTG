# Collect Board-View Documentation

|ID          |
|------------|
|CHSTG-INFO-04|

## Summary

This control aims to locate boardview documentation of the motherboard using the exact board reference identified previously. The objective is to identify the existence and availability of the physical layout files of the motherboard for later hardware analysis without performing any physical interaction with the device.

## Test Objectives
- Identify motherboard boardview documentation
- Determine availability of physical board layout files
- Identify sources providing access to boardview files

## How to Test
1. Use the motherboard reference identified during test CHSTG-INFO-01.

2. Perform online searches combining the board reference with keywords such as:
   - boardview
   - board view
   - motherboard boardview
   - pcb layout

Example searches (reference from CHSTG-INFO-01 test):

- `DAXK9FMB6C0 boardview`
  ![DAXK9FMB6C0 boardview](img/123.png)

- `DA0X8IMB8E0 boardview`
  ![DA0X8IMB8E0 boardview](img/00071854.png)

- `NB6099C_PCB_MB_MP1.0 boardview`  
  No result found (illustrating the absence of public schematic documentation for certain models).

3. Review search results to determine whether boardview documentation exists.

4. Identify the type of access required:
   - Publicly accessible files
   - Paid download
   - Restricted or VIP access platforms

5. Document the availability and access conditions for later use.

## Remediation
Not applicable.
