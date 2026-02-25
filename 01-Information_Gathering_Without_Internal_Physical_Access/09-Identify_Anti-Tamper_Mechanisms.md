# Identify Anti-Tamper Mechanisms

|ID          |
|------------|
|CHSTG-INFO-09|

## Summary

This control aims to visually identify potential anti-tamper protections using publicly available high-resolution motherboard images and previously collected documentation. The objective is to determine whether the device includes physical intrusion detection or protection mechanisms without physically accessing the system.

## Test Objectives
- Identify presence of tamper detection mechanisms
- Identify protection components related to intrusion detection
- Correlate protection mechanisms with previously collected hardware information

## How to Test
1. Use the motherboard reference identified during test CHSTG-INFO-01.

2. Collect high-resolution motherboard images from:
   - Spare parts reseller websites
   - Repair marketplaces
   - Technical forums

3. Analyze images to identify possible anti-tamper mechanisms such as:
   - Intrusion detection switches
   - Tamper detection circuits
   - Chassis opening sensors

Examples:

- **Dell Latitude 5420:**  
High-resolution image available at:  
https://laptopmedia.com/highlights/inside-dell-latitude-14-5420-disassembly-and-upgrade-options/  
![Dell_Latitude_5420](img/dell_latitude_5420.png)  
The anti-intrusion mechanism is easily identifiable as contact pads located near the edge of the motherboard.

- **HP EliteBook x360 830 G8:**  
High-resolution image available at:  
https://laptopmedia.com/highlights/inside-hp-elitebook-830-g8-disassembly-and-upgrade-options/  
![hp_elitebook_830_g8](img/hp_elitebook_830_g8.png)  
Here, the anti-tamper mechanism appears as two switches placed on either side of the chassis, clearly visible in the picture.


4. Correlate observations with previously collected information (component identification and documentation) to confirm the presence of protection mechanisms.

5. Document the identified protections for later analysis steps.

## Remediation
Not applicable.


