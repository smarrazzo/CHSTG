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

Example:

- **HP ProBook 430 G6**  
![HP ProBook 430 G6 disassembled](img/HP_430_Disass.png)  
The HP ProBook 430 G6 shown here is completely disassembled yet remains fully functional.

- **Dell Latitude 5420**  
![Dell Latitude 5420 disassembled](img/Dell_5420_disass.png)  
The Dell Latitude 5420, also completely disassembled, continues to operate normally.

These two examples illustrate that some systems can remain operational even after full chassis disassembly, highlighting the possible absence of hardware protections that restrict operation outside the enclosure.

5. Document whether the device operates fully while disassembled.

## Remediation
Enable all available anti-tamper protections in BIOS/UEFI settings. Note that such protections may still be bypassed depending on implementation.