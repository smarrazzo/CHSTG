# Assess System Operation While Fully Disassembled

|ID          |
|------------|
|CHSTG-PHY-05|

## Summary

This control aims to determine whether the system remains fully operational while completely disassembled. The objective is to assess whether the device can function normally outside of its chassis, which may indicate limited physical protection enforcement.

## Test Objectives
- Verify whether the system boots while fully disassembled
- Confirm whether hardware protections prevent operation outside the chassis
- Assess reliance on chassis-based security mechanisms

## How to Test
1. Fully disassemble the device according to standard procedures.

2. Reconnect only the necessary components required for system operation (e.g., motherboard, power supply, display connection if applicable).

3. Power on the system.

4. Observe system behavior:
   - Does the system boot normally?
   - Does the system detect chassis intrusion?
   - Is system functionality restricted?

5. Document whether the device operates fully while disassembled.

## Remediation
Enable all available anti-tamper protections in BIOS/UEFI settings. Note that such protections may still be bypassed depending on implementation.