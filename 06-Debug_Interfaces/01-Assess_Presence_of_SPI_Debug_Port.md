# Assess Presence of SPI Debug Port

|ID          |
|------------|
|CHSTG-DEBUG-01|

## Summary

This control aims to determine whether a dedicated SPI debug port is present on the motherboard. Identification may be performed through schematic and boardview analysis or by direct visual inspection of the motherboard. The objective is to assess the exposure of SPI debugging or programming interfaces.

## Test Objectives
- Identify presence of an SPI debug or programming interface
- Locate potential SPI-related connectors, headers, or test pads
- Assess exposure level of the SPI bus for debugging purposes

## How to Test
1. Review available documentation:
   - Schematic files
   - Boardview files

   Identify connectors or test points associated with SPI signals (e.g., CLK, MOSI, MISO, CS).

2. Perform direct visual inspection of the motherboard:
   - Look for unpopulated pin headers
   - Identify labeled test pads
   - Check for connectors marked SPI, DEBUG, JTAG, or similar

Example:
- **Dell Latitude 7280**
![Dell Latitude 7280](img/SPI_port.png)
On the Dell Latitude 7280, the SPI debug port is clearly identifiable thanks to the *JSPI1* marking on the motherboard, located near the BIOS chip.  

3. If signal observation is within authorized scope, assess whether protocol activity could be observed using:
   - Pogo probe systems (e.g., PCBite)
   - A logic analyzer (e.g., Saleae, DSLogic)

4. Document:
   - Presence or absence of an SPI debug interface
   - Physical location
   - Accessibility level
   - Documentation references (if identified via schematic/boardview)

## Remediation
Not applicable.


