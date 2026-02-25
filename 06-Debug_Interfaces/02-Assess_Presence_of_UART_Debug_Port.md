# Assess Presence of UART Debug Port

|ID          |
|------------|
|CHSTG-DEBUG-02|

## Summary

This control aims to determine whether a dedicated UART debug port is present on the motherboard. Identification may be performed through schematic and boardview analysis or by direct visual inspection of the motherboard. The objective is to assess the exposure of UART-based debugging interfaces.

## Test Objectives
- Identify presence of a UART debug interface
- Locate potential UART headers, pads, or connectors
- Assess exposure level of serial debug access

## How to Test
1. Review available documentation:
   - Schematic files
   - Boardview files

   Identify signals typically associated with UART communication (e.g., TX, RX, GND, VCC).

2. Perform direct visual inspection of the motherboard:
   - Look for unpopulated headers or pin pads
   - Identify labels such as UART, TX, RX, DEBUG, CONSOLE, Jx connectors
   - Locate test pads near embedded controller, SoC, or firmware components

Example:
- **Dell Latitude 7280**
![Dell Latitude 7280](img/UART_port.png)
On the Dell Latitude 7280, the UART debug port is clearly identifiable thanks to the *JUART1* marking on the motherboard.

3. If signal observation is within authorized scope, assess whether serial communication activity could be observed using:
   - Pogo probe systems (e.g., PCBite)
   - A logic analyzer (e.g., Saleae, DSLogic)

4. Document:
   - Presence or absence of a UART debug interface
   - Physical location
   - Accessibility level
   - Documentation references (if identified via schematic/boardview)

## Remediation
Not applicable.