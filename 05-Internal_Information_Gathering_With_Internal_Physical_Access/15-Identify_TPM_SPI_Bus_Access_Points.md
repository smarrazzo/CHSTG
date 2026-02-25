# Identify TPM SPI Bus Access Points

|ID          |
|------------|
|CHSTG-INT-15|

## Summary

This control aims to identify potential access points to the TPM communication bus (SPI or I2C), either through documentation review or physical signal analysis. The objective is to determine whether the TPM communication interface is exposed or accessible at the hardware level.

## Test Objectives
- Identify TPM communication interface type (SPI or I2C)
- Locate potential bus access points on the motherboard
- Assess exposure of TPM communication traces
- Evaluate feasibility of physical signal access

## How to Test
1. Identify the exact TPM chip reference (from CHSTG-INT-14).

2. Review the chip datasheet, if available, to determine:
   - Communication interface type (SPI or I2C)
   - Pinout configuration
   - Signal names (CLK, MOSI, MISO, CS, SDA, SCL, etc.)

3. Inspect the motherboard to locate:
   - Corresponding signal traces
   - Test pads
   - Unpopulated headers
   - Accessible vias

4. If performing signal observation within scope authorization, assess whether probing could theoretically be achieved using:
   - Pogo probe systems (e.g., PCBite)
   - Logic analyzers with bandwidth above 100 MHz (e.g., Saleae, DSLogic)

5. Document:
   - Identified bus type
   - Location of potential access points
   - Physical accessibility level
   - Overall exposure assessment (Low / Medium / High)

## Remediation
Apply epoxy resin over sensitive components and exposed bus traces to prevent physical probing and unauthorized signal access.-