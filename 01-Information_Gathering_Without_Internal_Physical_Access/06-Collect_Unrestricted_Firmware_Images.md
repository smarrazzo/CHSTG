# Collect Unrestricted Firmware Images

|ID          |
|------------|
|CHSTG-INFO-06|

## Summary

This control aims to identify the existence of unrestricted firmware versions or documented methods allowing password removal. The objective is to prepare future analysis by determining whether access restrictions can be bypassed using publicly documented techniques, without interacting physically with the device.

## Test Objectives
- Identify modified or unrestricted firmware versions
- Identify documented password removal methods
- Evaluate risks associated with unofficial firmware usage
- Prefer solutions based on the original device firmware

## How to Test
1. Use the exact device model identified during test CHSTG-INFO-01.

2. Perform online searches combining the model with keywords such as:
   - bios unlock
   - password removal
   - supervisor password reset
   - unlocked bios
   - modded firmware

3. Identify two possible approaches:
   - Modified firmware images removing restrictions
   - Documented procedures allowing password removal using the original firmware

4. Prioritize documented removal methods over modified firmware images, as modified firmware may not exactly match the hardware revision and may introduce risks.

Example:
For HP ProBook systems, documented methods exist:
https://gist.github.com/schorschii/752b3a06f7bc3b33ce7b65ff22c27337

5. Document the identified techniques and associated risks for later use.

## Remediation
Not applicable.
