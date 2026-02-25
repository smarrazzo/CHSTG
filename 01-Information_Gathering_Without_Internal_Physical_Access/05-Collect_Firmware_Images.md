# Collect Firmware Images

|ID          |
|------------|
|CHSTG-INFO-05|

## Summary

This control aims to identify and collect the available firmware images and their versions using the device reference on the manufacturer’s website. The objective is to prepare later analysis steps by knowing which firmware versions exist for the device without interacting physically with the system.

## Test Objectives
- Identify available firmware versions for the device
- Locate official firmware images
- Determine firmware update history

## How to Test
1. Use the exact device model identified during test CHSTG-INFO-01.

2. Access the manufacturer’s official support website.

3. Search for the device using:
   - Model name
   - Product number
   - Serial or service tag (if supported)

4. Navigate to the firmware or BIOS download section.

5. Identify and record:
   - Available firmware versions
   - Release dates
   - Downloadable firmware images

6. Archive the information for later analysis.

## Remediation
Not applicable.
