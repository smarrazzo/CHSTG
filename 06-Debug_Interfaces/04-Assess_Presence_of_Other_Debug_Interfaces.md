# Assess Presence of Other Debug Interfaces

|ID          |
|------------|
|CHSTG-DEBUG-04|

## Summary

This control aims to determine whether additional debug interfaces are present on the motherboard beyond SPI, UART, or JTAG. Identification may be performed through schematic and boardview analysis or by direct visual inspection. The objective is to assess overall exposure of hardware-level debugging interfaces.

## Test Objectives
- Identify presence of additional debug interfaces
- Locate potential headers, pads, or connectors linked to debugging
- Assess exposure level of undocumented or secondary debug access points

## How to Test
1. Review available documentation:
   - Schematic files
   - Boardview files

   Identify connectors or signals associated with alternative debug protocols (e.g., SWD, eSPI debug, manufacturer-specific debug headers).

2. Perform direct visual inspection of the motherboard:
   - Look for unpopulated pin headers or grouped test pads
   - Identify silkscreen labels such as DEBUG, TEST, SWD, CNx, Jx
   - Inspect areas near SoC, EC, chipset, or security components

3. If signal observation is within authorized scope, assess whether activity could theoretically be observed using:
   - Pogo probe systems (e.g., PCBite)
   - A logic analyzer (e.g., Saleae, DSLogic)

4. Document:
   - Presence or absence of additional debug interfaces
   - Physical location
   - Accessibility level
   - Documentation references (if identified via schematic/boardview)

## Remediation
Not applicable.