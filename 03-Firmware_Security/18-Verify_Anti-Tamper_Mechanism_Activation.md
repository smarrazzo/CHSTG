# Verify Anti-Tamper Mechanism Activation

|ID          |
|------------|
|CHSTG-FIRM-18|

## Summary

This control aims to verify whether firmware-level anti-tamper mechanisms, such as chassis opening detection, are enabled after obtaining BIOS/UEFI access (e.g., via CHSTG-FIRM-01 or CHSTG-FIRM-06 without firmware modification). The objective is to determine whether the system detects and logs physical intrusion events.

## Test Objectives
- Identify presence of chassis intrusion detection mechanisms
- Verify whether anti-tamper features are enabled
- Confirm whether intrusion events are logged or reported

## How to Test
1. Access the BIOS/UEFI configuration interface (without modifying firmware).

2. Navigate to security or hardware monitoring sections.

3. Identify configuration options related to anti-tamper mechanisms, such as:
   - Cover Removal Sensor
   - Chassis Intrusion Detection
   - Firmware Device Tamper Detection

4. Verify whether these mechanisms are:
   - Present
   - Enabled
   - Configurable

5. If supported by the firmware interface, check whether intrusion events are logged or indicated.

6. Document the activation status and configuration.

## Remediation
Enable all available anti-tamper and chassis intrusion detection mechanisms in BIOS/UEFI settings to ensure physical access attempts are detected and recorded.