# Execute Cold Boot Acquisition via Same-System USB Dump

|ID          |
|------------|
|CHSTG-MEM-02|

## Summary

This control evaluates the feasibility of performing a cold boot attack without moving the RAM modules to a different machine. By physically cooling the RAM to extreme temperatures, an attacker can force a reboot and boot the same system into a specialized USB environment to dump the memory contents. This technique is often used when RAM is difficult to remove or when a secondary compatible system is unavailable. A critical hurdle in this attack is the BIOS/UEFI "Memory Overwrite Request" (MOR), which must be bypassed or patched to prevent the firmware from wiping the RAM during the boot sequence.

## Test Objectives
- Demonstrate that memory data persists across a warm or cold reboot when the RAM is sufficiently cooled.
- Successfully bypass or neutralize the BIOS-level Memory Overwrite Request (MOR) variable.
- Acquire a full RAM dump using a USB-based UEFI tool on the original target hardware.

## How to Test
This test is performed directly on the target system. It requires the ability to trigger a reboot and access the boot menu.

### Prerequisites
- Access to the system's internal RAM (via a maintenance hatch or by removing the bottom cover) without full disassembly.
- A USB drive containing a UEFI-based dump tool such as **Memory-Dump-UEFI** or **ram-dump-efi**.

### Execution Steps
1.  **Cooling:** While the system is running or in a sleep state, use a compressed air duster held upside down to spray the RAM modules directly, lowering the temperature to approximately **-60°C**.
2.  **Forced Reboot:** Abruptly power cycle the machine (e.g., holding the power button or quickly disconnecting and reconnecting the battery/power).
3.  **MOR Bit Patching:** If the BIOS attempts to wipe memory, use a specialized tool or script to patch the **Memory Overwrite Request (MOR)** NVRAM variable to `0`. This informs the BIOS that no wipe is required on the next boot.
4.  **Boot to USB:** Immediately trigger the boot menu and select the USB drive containing the UEFI dump environment.
5.  **Acquisition:**
    - Launch the dump utility from the UEFI shell (e.g., `Memory-Dump-UEFI`).
    - Copy the physical memory range to the USB storage.
    - **Success Criteria:** An exploitable memory dump is obtained that contains remnants of the previous OS session (e.g., cleartext strings, process headers).

## Remediation
- **Memory Encryption:** Enable hardware-based RAM encryption such as **Intel Total Memory Encryption (TME)** or **AMD Transparent SME (TSME)** to ensure that data remains encrypted even if the physical charges are preserved.
- **Memory Scrambling:** Enable BIOS-level memory scrambling to obfuscate data patterns in the DRAM cells.
