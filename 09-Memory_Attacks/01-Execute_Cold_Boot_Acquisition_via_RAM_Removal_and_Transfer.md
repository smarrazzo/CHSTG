# Execute Cold Boot Acquisition via RAM Removal and Transfer

|ID          |
|------------|
|CHSTG-MEM-01|

## Summary

The "Cold Boot" attack exploits the physical property of DRAM, where data does not disappear instantly when power is removed. At room temperature, data remanence lasts only a few seconds, but by freezing the memory chips, the retention period can be extended to several minutes. This control evaluates the risk of an attacker physically removing the RAM modules from a running or recently powered-off system to dump their contents on a secondary machine, thereby bypassing OS-level memory protections and acquiring sensitive data like encryption keys or credentials.

## Test Objectives
- Demonstrate data remanence in DRAM by lowering the operating temperature.
- Successfully transfer "frozen" RAM modules to a receiver system without data loss.
- Perform a full memory acquisition using a minimal pre-OS environment on the receiver machine.

## How to Test
This test involves physical manipulation of the RAM modules and requires a secondary "receiver" machine with compatible memory slots.

### Prerequisites
- A target system with removable RAM modules (SO-DIMM or DIMM).
- A receiver system with the same RAM characteristics (e.g., DDR4, DDR5).
- A USB drive containing a UEFI-based dump tool such as **Memory-Dump-UEFI** or **ram-dump-efi**.

### Execution Steps
1.  **Preparation:** Have the receiver system open and ready to accept the RAM modules.
2.  **Freezing:** With the target system running (or in a sleep state), use a compressed air duster held upside down to spray the RAM chips. This can lower the temperature to approximately **-60°C**.
3.  **Power Cut:** Abruptly power off the target system by removing the battery and unplugging the power supply to prevent the BIOS from performing a memory wipe.
4.  **Transfer:** Quickly remove the RAM modules from the target system and install them into the receiver system.
5.  **Acquisition:**
    - Power on the receiver system and boot immediately into the USB UEFI shell.
    - Run the dump tool (e.g., `Memory-Dump-UEFI`) to copy the contents of the transferred RAM to the USB drive.
    - **Success Criteria:** A `.bin` or `.raw` image of the memory is obtained and contains readable strings or structures from the target system's session.

## Remediation
- **Memory Encryption:** Enable hardware-based memory encryption features such as **Intel Total Memory Encryption (TME)** or **AMD Transparent SME (TSME)**. This ensures that even if data is recovered from the chips, it remains encrypted and unreadable.
- **Memory Scrambling:** Ensure memory scrambling is enabled in the BIOS to prevent simple patterns from being easily reconstructed.
- **TCG MOR Bit:** Implement the **Memory Overwrite Request (MOR)** bit support, which instructs the BIOS to overwrite memory during boot if the OS did not shut down cleanly.
