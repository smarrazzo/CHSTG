# Verify Whether System Memory Is Soldered

|ID          |
|------------|
|CHSTG-INT-04|

## Summary

This control aims to determine whether the system memory (RAM) is soldered directly onto the motherboard or installed as removable modules. The objective is to assess the physical replaceability of system memory.

## Test Objectives
- Identify whether RAM is soldered to the motherboard
- Determine presence of removable memory modules
- Assess physical memory replaceability

## How to Test
1. Open the device according to standard disassembly procedures.

2. Visually inspect the memory area on the motherboard.

3. Determine whether:
   - Memory chips are soldered directly onto the motherboard
   - Removable memory modules (e.g., SO-DIMM) are present

Examples:

- **HP EliteBook x360 830 G8**  
![HP EliteBook x360 830 G8](imgs/HP_solder_ram.png)  
On the HP EliteBook x360 830 G8, the RAM is soldered to the motherboard and protected behind a clipped shield. There is no possibility for replacement or expansion.

- **Lenovo ThinkPad X1 Carbon Gen6**  
![Lenovo Thinkpad X1 Carbon Gen6](imgs/lenovo_Inaccesible_ram.png)  
On the Lenovo ThinkPad X1 Carbon Gen6, the RAM is soldered and difficult to access: removing the cover is not enough, it is necessary to remove the keyboard to access the memory.

- **Dell Latitude 7280**  
![Dell Latitude 7280](imgs/DELL_removable_ram.png)  
On the Dell Latitude 7280, the RAM is immediately accessible and uses the SO-DIMM format, which allows for easy removal and replacement.

4. Document the memory configuration (fully soldered, fully removable, or hybrid configuration).

## Remediation
Not applicable.