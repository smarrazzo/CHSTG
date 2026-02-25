# Assess USB4 Presence

|ID          |
|------------|
|CHSTG-INFO-13|

## Summary

This control aims to determine whether the device includes a USB4 port using external visual inspection and publicly available commercial and technical documentation. The objective is to confirm the presence of this interface without physically interacting with the system.

## Test Objectives
- Identify presence of a USB4 port
- Confirm port type using official documentation
- Correlate visual observations with technical specifications

## How to Test
1. Perform an external visual inspection of the device:
   - Look for USB logos indicating USB4 capability
   - Identify USB-C ports that may support USB4

The presence of a specific USB4 logo near a USB-C port may indicate that the port supports the USB4 interface. Here is an example of such a logo:
![USB4 Logo](img/USB4.jpg)
(Source: Official document https://www.usb.org/sites/default/files/D1T2-1%20-%20USB%20Branding%20Session.pdf)

However, it is always recommended to verify the manufacturer's technical documentation to confirm USB4 compatibility, as some USB-C ports may not support all USB4 features even if they display a similar logo.

2. Use the exact device model identified during test CHSTG-INFO-01.

3. Consult manufacturer commercial and technical documentation:
   - Product specification sheets
   - User manuals
   - Port diagrams

4. Confirm whether the USB-C port corresponds to:
   - Standard USB-C
   - USB4 interface

5. Document the presence or absence of USB4 for later analysis.

## Remediation
Not applicable.
